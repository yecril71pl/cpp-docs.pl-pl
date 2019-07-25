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
ms.openlocfilehash: d19d47fe7120301740e1431765fc6edbeaa48c60
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448191"
---
# <a name="sclsecurenowarnings"></a>_SCL_SECURE_NO_WARNINGS

Wywołanie dowolnych potencjalnie niebezpiecznych metod w C++ standardowej bibliotece skutkuje ostrzeżeniem [kompilatora (poziom 3) C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Aby wyłączyć to ostrzeżenie, zdefiniuj _SCL_SECURE_NO_WARNINGS makr w kodzie:

```cpp
#define _SCL_SECURE_NO_WARNINGS
```

Jeśli używasz prekompilowanych nagłówków, umieść tę dyrektywę we wstępnie skompilowanym pliku nagłówkowym przed uwzględnieniem dowolnej biblioteki środowiska uruchomieniowego języka C lub nagłówków biblioteki standardowej. Jeśli umieścisz ją w pliku kodu źródłowego przed dołączeniem prekompilowanego pliku nagłówkowego, zostanie on zignorowany przez kompilator.

## <a name="remarks"></a>Uwagi

Inne sposoby wyłączenia ostrzeżenia C4996 obejmują:

- Przy użyciu [/d (Definicje preprocesora)](../build/reference/d-preprocessor-definitions.md) opcja kompilatora:

   > CL/D_SCL_SECURE_NO_WARNINGS [inne opcje kompilatora] plik. cpp

- Przy użyciu [/w](../build/reference/compiler-option-warning-level.md) opcji kompilatora:

   > CL/wd4996 [inne opcje kompilatora] plik. cpp

- Za pomocą dyrektywy [ostrzegawczej #pragma](../preprocessor/warning.md) :

   ```cpp
   #pragma warning(disable:4996)
   ```

Ponadto można ręcznie zmienić poziom ostrzeżeń C4996 z opcją **/w\<l\<> n >** kompilatora. Na przykład, aby ustawić ostrzeżenie C4996 na poziomie 4:

> CL/w44996 [inne opcje kompilatora] plik. cpp

Aby uzyskać więcej informacji, zobacz [/w,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżeń)](../build/reference/compiler-option-warning-level.md).

## <a name="see-also"></a>Zobacz także

[Bezpieczne biblioteki: Standardowa biblioteka C++](../standard-library/safe-libraries-cpp-standard-library.md)
