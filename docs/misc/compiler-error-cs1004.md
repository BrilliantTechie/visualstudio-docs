---
title: "Compiler Error CS1004"
ms.custom: na
ms.date: "10/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "CS1004"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1004"
ms.assetid: 93cc1b93-ca4c-49a8-af03-9fbfc84ccab9
caps.latest.revision: 6
ms.author: "billchi"
manager: "douge"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# Compiler Error CS1004
Duplicate 'modifier' modifier  
  
 A duplicate modifier, such as an **access** modifier, was detected.  
  
 The following sample generates CS1004:  
  
```  
// CS1004.cs  
public class clx  
{  
   public public static void Main()   // CS1004, two public keywords  
   {  
   }  
}  
```