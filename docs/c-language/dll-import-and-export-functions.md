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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62234250"
---
# <a name="dll-import-and-export-functions"></a>Importowanie bibliotek DLL i eksportowanie funkcji

**Specyficzne dla firmy Microsoft**

Najbardziej kompletne i aktualne informacje na ten temat można znaleźć w [dllexport, dllimport](../cpp/dllexport-dllimport.md).

Modyfikatory klasy `dllexport` **dllimport** i magazynu są rozszerzeniami specyficznymi dla firmy Microsoft do języka C. Te Modyfikatory jawnie definiują interfejs biblioteki DLL dla klienta (plik wykonywalny lub inna Biblioteka DLL). Deklarowanie funkcji `dllexport` jako eliminuje potrzebę definicji modułów (. DEF). Można również użyć elementu **dllimport** i `dllexport` modyfikatorów z danymi i obiektami.

Modyfikatory **dllimport** i `dllexport` klasy magazynu muszą być używane z słowem kluczowym `__declspec`składni atrybutów rozszerzonych, jak pokazano w poniższym przykładzie:

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllExport int j;
DllExport int n;
```

Aby uzyskać szczegółowe informacje na temat składni dla rozszerzonych modyfikatorów klasy magazynu, zobacz [rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md).

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
