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
ms.openlocfilehash: b4f0674e68f2c7b8deeae663c42470b83777ac78
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572393"
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

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)