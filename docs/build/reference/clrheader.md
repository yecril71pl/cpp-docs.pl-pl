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
ms.openlocfilehash: 6a1240e2d3ad2ac3a454c610a6f49d07e50951e5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820705"
---
# <a name="clrheader"></a>/CLRHEADER

Wyświetl informacje specyficzne dla środowiska CLR.

## <a name="syntax"></a>Składnia

> / CLRHEADER *pliku*

### <a name="arguments"></a>Argumenty

*Plik*<br/>
Plik obrazu utworzonych za pomocą [/CLR](clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Uwagi

**/ CLRHEADER** wyświetla informacji o nagłówkach .NET, używany w żadnym programie zarządzanych. Dane wyjściowe pokazują lokalizację i rozmiar w bajtach nagłówka .NET i sekcjach w nagłówku.

Tylko [/HEADERS](headers.md) — opcja polecenia DUMPBIN jest dostępna do użycia w plikach z [/GL](gl-whole-program-optimization.md) — opcja kompilatora.

Gdy **/CLRHEADER** jest używany w pliku, który został skompilowany z/CLR, nastąpi **nagłówka clr:** sekcji w danych wyjściowych polecenia dumpbin. Wartość **flagi** wskazuje użyto opcji/CLR:

- 0 — / CLR (obraz może zawierać kod natywny).

Można także programowo sprawdzać, jeśli obraz został zbudowany dla środowiska uruchomieniowego języka wspólnego.  Aby uzyskać więcej informacji, zobacz [jak: Określić, czy obraz jest obrazem natywnym, czy CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Kod, który musi być "czysta" lub "bezpieczne" powinny być przenoszone do C#.

## <a name="see-also"></a>Zobacz także

- [Opcje DUMPBIN](dumpbin-options.md)
