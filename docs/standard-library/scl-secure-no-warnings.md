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
ms.openlocfilehash: b24012825b883550de6f58e6ce2d53b826f746ca
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965503"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Wywoływanie metod potencjalnie niebezpiecznych w standardowej biblioteki C++ powoduje [ostrzeżenie kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Aby wyłączyć to ostrzeżenie, należy zdefiniować _SCL_SECURE_NO_WARNINGS makra w kodzie:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Jeśli używasz wstępnie skompilowanych nagłówków, należy umieścić tej dyrektywy w pliku wstępnie skompilowanego nagłówka przed wprowadzeniem wszystkie biblioteki wykonawczej języka C lub nagłówki standardowej biblioteki. Jeśli umieścisz go w pliku kodu źródłowego poszczególnych przed wprowadzeniem prekompilowanego pliku nagłówkowego, jest on ignorowany przez kompilator.

## <a name="remarks"></a>Uwagi

Inne sposoby, aby wyłączyć ostrzeżenia C4996 obejmują:

- Za pomocą [/D (definicje preprocesora)](../build/reference/d-preprocessor-definitions.md) — opcja kompilatora:

   > myfile.cpp /D_SCL_SECURE_NO_WARNINGS [inne opcje kompilatora] cl

- Za pomocą [Wn](../build/reference/compiler-option-warning-level.md) — opcja kompilatora:

   > Cl /wd4996 [inne opcje kompilatora] myfile.cpp

- Za pomocą [ostrzeżenie #pragma](../preprocessor/warning.md) dyrektywy:

   ```cpp
   #pragma warning(disable:4996)
   ```

Ponadto, możesz ręcznie zmienić poziom ostrzeżenia C4996 z **Wn\<l >\<n >** — opcja kompilatora. Na przykład, aby ustawić ostrzeżenie C4996 poziom 4:

> Cl /w44996 [inne opcje kompilatora] myfile.cpp

Aby uzyskać więcej informacji, zobacz [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Zobacz także

[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)<br/>
