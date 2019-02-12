---
title: Importowanie bibliotek DLL i eksportowanie funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- DLLs [C++], importing
- dllimport attribute [C++], storage-class attribute
- DLL exports [C++]
- declaring functions, with dllexport and dllimport
- extended storage-class attributes
- dllexport attribute [C++], storage-class attribute
ms.assetid: 08d164b9-770a-4e14-afeb-c6f21d9e33e4
ms.openlocfilehash: 8d703045773e4d2c320eaef2aa80c4ce74d23472
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149313"
---
# <a name="dll-import-and-export-functions"></a>Importowanie bibliotek DLL i eksportowanie funkcji

**Microsoft Specific**

Najbardziej kompletne i aktualne informacje na ten temat można znaleźć w [dllexport i dllimport](../cpp/dllexport-dllimport.md).

**Dllimport** i `dllexport` modyfikatorów klasy magazynowania są specyficzne dla Microsoft rozszerzenia języka C. Tych modyfikatorów jawnie definiują interfejs DLL dla jego klienta (plik wykonywalny lub innej biblioteki DLL). Deklarowanie funkcji jako `dllexport` eliminuje potrzebę stosowania definicji modułów (. Plik DEF). Można również użyć **dllimport** i `dllexport` Modyfikatory przy użyciu danych i obiektów.

**Dllimport** i `dllexport` modyfikatorów klasy magazynowania, należy użyć za pomocą słowa kluczowego składni atrybutów rozszerzonych, `__declspec`, jak pokazano w poniższym przykładzie:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllExport int j;
DllExport int n;
```

Aby uzyskać szczegółowe informacje o składni modyfikatorów klasy magazynowania rozszerzonej, zobacz [rozszerzone atrybuty klasy magazynowania](../c-language/c-extended-storage-class-attributes.md).

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
