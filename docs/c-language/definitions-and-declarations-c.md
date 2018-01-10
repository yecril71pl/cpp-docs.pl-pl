---
title: Definicje i Declarations (C) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4886ee6a8bce115c2f7676124477ec81e71b16d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="definitions-and-declarations-c"></a>Definicje i deklaracje (C)
**Dotyczące firmy Microsoft**  
  
 Interfejsu biblioteki DLL odwołuje się do wszystkich elementów (funkcje i dane), które są znane do wyeksportowania przez program w systemie; oznacza to, że wszystkie elementy, które są zadeklarowane jako **dllimport** lub `dllexport`. Wszystkie deklaracje objęte interfejsu biblioteki DLL należy określić albo **dllimport** lub `dllexport` atrybutu. Jednak definicji można określić tylko `dllexport` atrybutu. Na przykład następujące definicji funkcji generuje błąd kompilatora:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int func()    /* Error; dllimport prohibited in */  
                        /* definition. */  
{  
   return 1;  
}  
```  
  
 Ten kod również generuje błąd:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllImport int i = 10;      /* Error; this is a definition. */  
```  
  
 Jednak jest to prawidłowa składnia:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport int i = 10;      /* Okay: this is an export definition. */  
```  
  
 Korzystanie z `dllexport` oznacza definicję, gdy **dllimport** oznacza deklaracji. Należy użyć `extern` — słowo kluczowe z `dllexport` Aby wymusić deklarację; w przeciwnym razie jest domniemane definicji.  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
extern DllImport int k;   /* These are correct and imply */  
Dllimport int j;          /* a declaration. */      
```  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie bibliotek DLL i eksportowanie funkcji](../c-language/dll-import-and-export-functions.md)