---
title: _SCL_SECURE_NO_WARNINGS
ms.date: 11/04/2016
f1_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
helpviewer_keywords:
- _SCL_SECURE_NO_DEPRECATE
- _SCL_SECURE_NO_WARNINGS
ms.assetid: ef0ddea9-7c62-4b53-8b64-5f4fd369776f
ms.openlocfilehash: 77c60aed511fc3dbbea2d74e83e36dae735dcb0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348311"
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
