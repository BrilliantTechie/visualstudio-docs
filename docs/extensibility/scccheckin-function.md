---
title: "SccCheckin Function"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "SccCheckin"
helpviewer_keywords: 
  - "SccCheckin function"
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
translation.priority.mt: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# SccCheckin Function
This function checks in previously checked-out files to the source control system, storing the changes and creating a new version. This function is called with a count and an array of names of the files to be checked in.  
  
## Syntax  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### Parameters  
 pvContext  
 [in] The source control plug-in context structure.  
  
 hWnd  
 [in] A handle to the IDE window that the SCC plug-in can use as a parent for any dialog boxes that it provides.  
  
 nFiles  
 [in] Number of files selected to be checked in.  
  
 lpFileNames  
 [in] Array of fully qualified local path names of files to be checked in.  
  
 lpComment  
 [in] Comment to be applied to each of the selected files being checked in. This is `NULL` if the source control plug-in should prompt for a comment.  
  
 fOptions  
 [in] Command flags, either 0 or `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] SCC plug-in-specific options.  
  
## Return Value  
 The source control plug-in implementation of this function is expected to return one of the following values:  
  
|Value|Description|  
|-----------|-----------------|  
|SCC_OK|Files was successfully checked in.|  
|SCC_E_FILENOTCONTROLLED|The selected file is not under source code control.|  
|SCC_E_ACCESSFAILURE|There was a problem accessing the source control system, probably due to network or contention issues. A retry is recommended.|  
|SCC_E_NONSPECIFICERROR|Nonspecific failure. File was not checked in.|  
|SCC_E_NOTCHECKEDOUT|The user has not checked out the file, so cannot check it in.|  
|SCC_E_CHECKINCONFLICT|Checkin could not be performed because:<br /><br /> -   Another user has checked in ahead and `bAutoReconcile` was false.<br /><br /> -or-<br /><br /> -   The auto-merge cannot be done (for example, when files are binary).|  
|SCC_E_VERIFYMERGE|File has been auto-merged but has not been checked in pending user verification.|  
|SCC_E_FIXMERGE|File has been auto-merged but has not been checked in due to a merge conflict that must be manually resolved.|  
|SCC_E_NOTAUTHORIZED|The user is not allowed to perform this operation.|  
|SCC_I_OPERATIONCANCELED|Operation was cancelled before completion.|  
|SCC_I_RELOADFILE|A file or project needs to be reloaded.|  
|SCC_E_FILENOTEXIST|Local file was not found.|  
  
## Remarks  
 The comment applies to all files being checked in. The comment argument can be a `null` string, in which case the source control plug-in can prompt the user for a comment string for each file.  
  
 The `fOptions` argument can be given a value of the `SCC_KEEP_CHECKEDOUT` flag to indicate the user's intent to check the file in and check it out again.  
  
## See Also  
 [Source Control Plug-in API Functions](../extensibility/source-control-plug-in-api-functions.md)