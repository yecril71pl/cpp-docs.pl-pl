---
title: Zmienne środowiskowe CL
ms.date: 06/06/2019
f1_keywords:
- cl
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 0f7930728ef1bf6bea50c4388d52d30c569a8795
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821533"
---
# <a name="cl-environment-variables"></a>Zmienne środowiskowe CL

Narzędzia CL są używane następujące zmienne środowiskowe:

- CL i \_CL_, jeśli została zdefiniowana. Narzędzia CL dołącza opcje i argumenty zdefiniowane w zmiennej środowiskowej CL do argumentów wiersza polecenia i dołącza opcje i argumenty zdefiniowane w \_CL_ przed rozpoczęciem przetwarzania.

- UWZGLĘDNIĆ, który musi się odnosić do podkatalogu \include instalację programu Visual Studio.

- LIBPATH, który określa katalogi do wyszukiwania plików metadanych, do którego odwołuje się [#using](../../preprocessor/hash-using-directive-cpp.md). Aby uzyskać więcej informacji na temat LIBPATH, zobacz [#using](../../preprocessor/hash-using-directive-cpp.md).

Możesz ustawić CL lub \_CL_ zmienną środowiskową przy użyciu następującej składni:

> Ustaw CL = [[*opcji*]... [*pliku*]...] [/ link *zoptymalizowany pod kątem linku* ...] \
> Ustaw \_CL\_= [[*opcji*]... [*pliku*]...] [/ link *zoptymalizowany pod kątem linku* ...]

Aby uzyskać szczegółowe informacje na temat argumentów cl i \_CL_ zmiennych środowiskowych, zobacz [składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md).

Te zmienne środowiskowe można użyć do definiowania plików i opcji, których używasz najczęściej. Następnie użyć wiersza polecenia, aby dać więcej plików i opcji cl do określonych celów. CL i \_CL_ zmienne środowiskowe są ograniczone do 1024 znaków (wiersza polecenia limit wejściowego).

Nie można użyć [/D](d-preprocessor-definitions.md) opcję, aby zdefiniować symbol, który używa znaku równości ( **=** ). Zamiast tego można użyć znak numeru ( **#** ) dla równości. W ten sposób można użyć CL lub \_CL_ zmiennych środowiskowych w celu definiowania stałych preprocesora z jawne wartości — na przykład `/DDEBUG#1` do definiowania `DEBUG=1`.

Aby uzyskać powiązane informacje, zobacz [ustawić zmienne środowiskowe](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Przykłady

Przykładem ustawienie zmiennej środowiskowej CL jest następujące polecenie:

> Ustaw CL = / Zp2 OX /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ

Kiedy ustawić zmiennej środowiskowej CL po wprowadzeniu `CL INPUT.C` w wierszu polecenia polecenie skuteczne staje się:

> CL /Zp2 OX /I\INCLUDE\MYINCLS \LIB\BINMODE. OBJ DANE WEJŚCIOWE. C

Poniższy przykład powoduje zwykły polecenie CL, aby skompilować pliki źródłowe FILE1.c i FILE2.c, a następnie połącz pliki obiektów FILE1.obj FILE2.obj i FILE3.obj:

> ZESTAW CL = FILE1. PLIK2 C. C \
> USTAW \_CL_ = PLIK3. OBJ \
> CL

Te zmienne środowiskowe wywoływania CL mają taki sam skutek jak następującego polecenia:

> PLIK1 CL. PLIK2 C. PLIK3 C. OBJ

## <a name="see-also"></a>Zobacz także

[Ustawianie opcji kompilatora](compiler-command-line-syntax.md) \
[Opcje kompilatora MSVC](compiler-options.md)
