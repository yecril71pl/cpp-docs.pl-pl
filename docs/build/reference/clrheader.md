---
title: /CLRHEADER
ms.date: 11/04/2016
f1_keywords:
- /CLRHEADER
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
ms.openlocfilehash: 864ecc0063716ce712e28b063714ce7c17fc294a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627373"
---
# <a name="clrheader"></a>/CLRHEADER

Wyświetl informacje specyficzne dla środowiska CLR.

## <a name="syntax"></a>Składnia

> / CLRHEADER *pliku*

### <a name="arguments"></a>Argumenty

|||
|-|-|
*Plik*| Plik obrazu utworzonych za pomocą [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Uwagi

**/ CLRHEADER** wyświetla informacji o nagłówkach .NET, używany w żadnym programie zarządzanych. Dane wyjściowe pokazują lokalizację i rozmiar w bajtach nagłówka .NET i sekcjach w nagłówku.

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

Gdy **/CLRHEADER** jest używany w pliku, który został skompilowany z/CLR, nastąpi **nagłówka clr:** sekcji w danych wyjściowych polecenia dumpbin. Wartość **flagi** wskazuje użyto opcji/CLR:

- 0 — / CLR (obraz może zawierać kod natywny).

Można także programowo sprawdzać, jeśli obraz został zbudowany dla środowiska uruchomieniowego języka wspólnego.  Aby uzyskać więcej informacji, zobacz [jak: ustalić, czy obraz jest obrazem natywnym, czy CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Kod, który musi być "czysta" lub "bezpieczne" powinny być przenoszone do C#.

## <a name="see-also"></a>Zobacz także

- [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)
