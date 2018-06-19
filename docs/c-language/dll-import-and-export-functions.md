---
title: Importowanie bibliotek DLL i eksportowanie funkcji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da456b7caca59fb874f4da87a342162b53c09319
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384957"
---
# <a name="dll-import-and-export-functions"></a>Importowanie bibliotek DLL i eksportowanie funkcji
**Microsoft Specific**  
  
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