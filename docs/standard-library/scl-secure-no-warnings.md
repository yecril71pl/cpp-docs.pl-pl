---
title: _SCL_SECURE_NO_WARNINGS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec02ce5aab3d8a7f95ec9020fe3e2a00c1f5bef7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854356"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Wywoływanie metod potencjalnie niebezpiecznych w standardowa biblioteka C++ powoduje [C4996 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Aby wyłączyć to ostrzeżenie, zdefiniuj makra **_SCL_SECURE_NO_WARNINGS** w kodzie:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Użycie prekompilowanych nagłówków, przed wprowadzeniem żadnych Biblioteka środowiska wykonawczego języka C lub nagłówki biblioteki standardowej umieść tej dyrektywy w pliku prekompilowanego nagłówka. Umieszczenie go w pliku kodu źródłowego poszczególnych przed wprowadzeniem prekompilowanego pliku nagłówkowego, jest ignorowana przez kompilator.

## <a name="remarks"></a>Uwagi

Inne sposoby wyłączenia ostrzeżenie C4996 obejmują:

- Przy użyciu [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md) — opcja kompilatora:

   > Cl myfile.cpp /D_SCL_SECURE_NO_WARNINGS [innych opcji kompilatora]

- Przy użyciu [/w](../build/reference/compiler-option-warning-level.md) — opcja kompilatora:

   > Cl /wd4996 [innych opcji kompilatora] myfile.cpp

- Przy użyciu [ostrzeżenie #pragma](../preprocessor/warning.md) dyrektywy:

   ```cpp
   #pragma warning(disable:4996)
   ```

Ponadto możesz ręcznie zmienić poziom ostrzeżenia C4996 z **/w\<l >\<n >** — opcja kompilatora. Na przykład, aby ustawić ostrzeżenie C4996 poziom 4:

> Cl /w44996 [innych opcji kompilatora] myfile.cpp

Aby uzyskać więcej informacji, zobacz [/w, /W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / możemy /wo, /Wv, wx (poziom ostrzegawczy)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Zobacz także

[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
