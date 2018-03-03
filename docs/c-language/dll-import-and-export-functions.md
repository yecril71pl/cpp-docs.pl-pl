---
title: Importowanie bibliotek DLL i eksportowanie funkcji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b79856a524cb9693d43d9929b22d6c63db5ba319
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dll-import-and-export-functions"></a>Importowanie bibliotek DLL i eksportowanie funkcji
**Dotyczące firmy Microsoft**  
  
 Najbardziej kompletne i aktualne informacje na ten temat można znaleźć w [dllexport i dllimport](../cpp/dllexport-dllimport.md).  
  
 **Dllimport** i `dllexport` Modyfikatory Klasa magazynu są rozszerzenia specyficzne dla firmy Microsoft dla języka C. Modyfikatory tych jawnie definiować interfejsu biblioteki DLL do klienta (plik wykonywalny lub innej bibliotece DLL). Deklarowanie funkcji jako `dllexport` eliminuje potrzebę stosowania definicji modułu (. Plik DEF). Można również użyć **dllimport** i `dllexport` Modyfikatory przy użyciu danych i obiektów.  
  
 **Dllimport** i `dllexport` Modyfikatory Klasa magazynu musi być używany z kluczowego składni rozszerzonych atrybutów `__declspec`, jak pokazano w poniższym przykładzie:  
  
```  
#define DllImport   __declspec( dllimport )  
#define DllExport   __declspec( dllexport )  
  
DllExport void func();  
DllExport int i = 10;  
DllExport int j;  
DllExport int n;  
```  
  
 Szczegółowe informacje dotyczące składnia Modyfikatory Klasa magazynu rozszerzonego, zobacz [rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md).  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Definicje funkcji języka C](../c-language/c-function-definitions.md)