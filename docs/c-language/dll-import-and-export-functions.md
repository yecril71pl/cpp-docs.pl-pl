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
ms.openlocfilehash: 3da47c4d6c5af518660b5799b3bf9ae3f512a6fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029224"
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