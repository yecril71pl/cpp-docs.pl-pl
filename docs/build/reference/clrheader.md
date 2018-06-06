---
title: -CLRHEADER | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRHEADER
dev_langs:
- C++
helpviewer_keywords:
- -CLRHEADER dumpbin option
- /CLRHEADER dumpbin option
- CLRHEADER dumpbin option
ms.assetid: cf73424f-4541-47e2-b94e-69b95266ef2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f6cda2f03e8a0473d2c45f54c96ca97b043d80d5
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704444"
---
# <a name="clrheader"></a>/CLRHEADER

Wyświetl informacje specyficzne dla środowiska CLR.

## <a name="syntax"></a>Składnia

> / CLRHEADER *pliku*

### <a name="arguments"></a>Argumenty

|||
|-|-|
*Plik*| Skompilowany plik obrazu [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="remarks"></a>Uwagi

**/ CLRHEADER** wyświetla informacji o nagłówkach .NET używane w programach zarządzanych. Dane wyjściowe zawierają lokalizację i rozmiar w bajtach nagłówka .NET i sekcji w nagłówku.

Tylko [/HEADERS](../../build/reference/headers.md) — opcja polecenia DUMPBIN jest dostępny do użytku na pliki tworzone z [/GL](../../build/reference/gl-whole-program-optimization.md) — opcja kompilatora.

Gdy **/CLRHEADER** jest używany w pliku, który został skompilowany z/CLR, będzie **clr nagłówka:** sekcji w danych wyjściowych polecenia dumpbin. Wartość **flagi** wskazuje użyto opcji/CLR:

- 0 — / CLR (obraz może zawierać kod natywny).

Można również programowane sprawdzanie, jeśli obraz został utworzony dla środowiska CLR.  Aby uzyskać więcej informacji, zobacz [porady: ustalić, czy obraz jest natywnym, czy CLR](../../dotnet/how-to-determine-if-an-image-is-native-or-clr.md).

**/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r. Kod, który musi być "czysty" lub "bezpiecznej" powinny być przenoszone do języka C#.

## <a name="see-also"></a>Zobacz także

- [Opcje DUMPBIN](../../build/reference/dumpbin-options.md)
