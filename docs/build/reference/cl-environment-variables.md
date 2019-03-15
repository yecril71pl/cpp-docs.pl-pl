---
title: Zmienne środowiskowe CL
ms.date: 11/04/2016
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: a15bedc0a5aa8215356a98c3635a2edd1f3cfc5f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807965"
---
# <a name="cl-environment-variables"></a>Zmienne środowiskowe CL

Narzędzia CL są używane następujące zmienne środowiskowe:

- CL i \_CL\_, jeśli została zdefiniowana. Narzędzia CL dołącza opcje i argumenty zdefiniowane w zmiennej środowiskowej CL do argumentów wiersza polecenia i dołącza opcje i argumenty zdefiniowane w \_CL\_, przed rozpoczęciem przetwarzania.

- UWZGLĘDNIĆ, który musi się odnosić do podkatalogu \include instalację programu Visual C++.

- LIBPATH, który określa katalogi do wyszukiwania plików metadanych, do którego odwołuje się [#using](../../preprocessor/hash-using-directive-cpp.md). Zobacz `#using` więcej informacji na temat LIBPATH.

Możesz ustawić CL lub \_CL\_ zmienną środowiskową przy użyciu następującej składni:

> Ustaw CL = [[*opcji*]... [*pliku*]...] [/ link *zoptymalizowany pod kątem linku* ...] Ustaw \_CL\_= [[*opcji*]... [*pliku*]...] [/ link *zoptymalizowany pod kątem linku* ...]

Aby uzyskać szczegółowe informacje na temat argumentów cl i \_CL\_ zmiennych środowiskowych, zobacz [składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md).

Można użyć tych zmiennych środowiskowych do definiowania plików i opcji, których używasz najczęściej i użyć wiersza polecenia, aby zdefiniować konkretne pliki i opcje do określonych celów. CL i \_CL\_ zmienne środowiskowe są ograniczone do 1024 znaków (wiersza polecenia limit wejściowego).

Nie można użyć opcji/d., aby zdefiniować symbol, który używa znaku równości (=). Można zastąpić znak numeru (#) znaku równości. W ten sposób można użyć CL lub \_CL\_ zmiennych środowiskowych w celu definiowania stałych preprocesora z jawne wartości — na przykład `/DDEBUG#1` do definiowania `DEBUG=1`.

Aby uzyskać powiązane informacje, zobacz [ustawić zmienne środowiskowe](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Przykłady

Oto przykład ustawienia zmiennej środowiskowej CL:

> Ustaw CL = / Zp2 OX /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ

Gdy ta zmienna środowiskowa jest ustawiona, po wprowadzeniu `CL INPUT.C` w wierszu polecenia jest skuteczne polecenie:

> CL /Zp2 OX /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ DANE WEJŚCIOWE. C

Poniższy przykład powoduje zwykły polecenie CL, aby skompilować pliki źródłowe FILE1.c i FILE2.c, a następnie połącz pliki obiektów FILE1.obj FILE2.obj i FILE3.obj:

> ZESTAW CL = FILE1. PLIK2 C. ZESTAW C \_CL\_= PLIK3. OBJ CL

Ma to taki sam skutek jak następującego polecenia:

> PLIK1 CL. PLIK2 C. PLIK3 C. OBJ

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji kompilatora](compiler-command-line-syntax.md)<br/>
[MSVC Compiler Options](compiler-options.md)
