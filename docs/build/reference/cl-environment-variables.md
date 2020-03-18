---
title: Zmienne środowiskowe CL
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 4d6b1982b1e544459a025d6cb7bee75666e7130e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440247"
---
# <a name="cl-environment-variables"></a>Zmienne środowiskowe CL

Narzędzie CL używa następujących zmiennych środowiskowych:

- CL i CL_ \_, jeśli zostały zdefiniowane. Narzędzie CL dołącza opcje i argumenty zdefiniowane w zmiennej środowiskowej CL do argumentów wiersza polecenia i dołącza opcje i argumenty zdefiniowane w \_CL_ przed przetworzeniem.

- Dołącz, który musi wskazywać podkatalog \Include w instalacji programu Visual Studio.

- LIBPATH, który określa katalogi do wyszukiwania plików metadanych, do których odwołuje się [#using](../../preprocessor/hash-using-directive-cpp.md). Aby uzyskać więcej informacji na temat LIBPATH, zobacz [#using](../../preprocessor/hash-using-directive-cpp.md).

Można ustawić zmienną środowiskową CL lub \_CL_ przy użyciu następującej składni:

> Ustaw CL = [*opcja*]... [*plik*]...] [/link *link-opt* ...] \
> Ustaw \_CL\_= [[*Option*]... [*plik*]...] [/link *link-opt* ...]

Aby uzyskać szczegółowe informacje na temat argumentów dla zmiennych środowiskowych CL i \_CL_, zobacz [składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md).

Te zmienne środowiskowe służą do definiowania plików i opcji, których najczęściej używasz. Następnie użyj wiersza polecenia, aby uzyskać więcej plików i opcji do CL do określonych celów. Zmienne środowiskowe CL i \_CL_ są ograniczone do 1024 znaków (limit wprowadzania w wierszu polecenia).

Nie można użyć [/d](d-preprocessor-definitions.md) opcji do zdefiniowania symbolu, który używa znaku równości ( **=** ). Zamiast tego można użyć znaku numeru ( **#** ) jako znaku równości. W ten sposób można użyć zmiennych środowiskowych CL lub \_CL_ do definiowania stałych preprocesora z jawnymi wartościami — na przykład `/DDEBUG#1` do definiowania `DEBUG=1`.

Aby uzyskać powiązane informacje, zobacz [Ustawianie zmiennych środowiskowych](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Przykłady

Następujące polecenie jest przykładem ustawienia zmiennej środowiskowej CL:

> SET CL =/Zp2/OX/I\INCLUDE\MYINCLS \LIB\BINMODE. OBIEKTÓW

Gdy zmienna środowiskowa CL jest ustawiona, w przypadku wprowadzenia `CL INPUT.C` w wierszu polecenia efektywne polecenie zmieni się na:

> CL/Zp2/OX/I\INCLUDE\MYINCLS \LIB\BINMODE. WEJŚCIE OBJ. S

Poniższy przykład powoduje, że polecenie "zwykły CL" kompiluje pliki źródłowe plik1. c i PLIK2. c, a następnie łączy pliki obiektów plik1. obj, PLIK2. obj i FILE3. obj:

> USTAW CL = PLIK1. C PLIK2. S
> Ustaw \_CL_ = FILE3. Obiektów
> CL

Te zmienne środowiskowe sprawiają, że wywołanie CL ma taki sam skutek jak w przypadku następującego wiersza polecenia:

> CL. C PLIK2. C FILE3. OBIEKTÓW

## <a name="see-also"></a>Zobacz też

[Ustawianie opcji kompilatora](compiler-command-line-syntax.md) \
[Opcje kompilatora MSVC](compiler-options.md)
