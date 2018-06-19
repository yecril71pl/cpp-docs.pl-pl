---
title: Definicje i Declarations (C) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d44a98fee82e41252b27fa5a1605b04a15af9115
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383488"
---
# <a name="definitions-and-declarations-c"></a>Definicje i deklaracje (C)
**Microsoft Specific**  
  
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