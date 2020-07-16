---
title: Błąd narzędzi konsolidatora LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 69a832716dffee4e024b3bb1a1f0de6ee8105e99
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404167"
---
# <a name="linker-tools-error-lnk2038"></a>Błąd narzędzi konsolidatora LNK2038

> wykryto niezgodność dla elementu "*name*": wartość "*value_1*" nie jest zgodna z wartością "*value_2*" w *pliku filename. obj*

Program łączący wykrył niezgodność symboli. Ten błąd wskazuje, że różne części aplikacji, w tym biblioteki lub inny kod obiektu, z którym łączy się aplikacja, używają definicji w konflikcie symboli. Dyrektywa pragma [wykrywania niezgodności](../../preprocessor/detect-mismatch.md) służy do definiowania takich symboli i wykrywania ich wartości powodujących konflikt.

## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania

Ten błąd może wystąpić, gdy plik obiektu w projekcie jest nieaktualny. Przed podjęciem próby wykonania innych rozwiązań tego błędu Wykonaj czystą kompilację, aby upewnić się, że pliki obiektów są aktualne.

Program Visual Studio definiuje następujące symbole, aby zapobiec łączeniu niezgodnego kodu, co może spowodować błędy w czasie wykonywania lub inne nieoczekiwane zachowanie.

- `_MSC_VER`Wskazuje główne i pomocnicze numery wersji kompilatora języka Microsoft C++ (MSVC), który jest używany do kompilowania aplikacji lub biblioteki. Kod kompilowany przy użyciu jednej wersji MSVC jest niezgodny z kodem, który jest kompilowany przy użyciu wersji, która ma inne główne i pomocnicze numery wersji. Aby uzyskać więcej informacji, zobacz `_MSC_VER` w obszarze [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

   Jeśli łączysz się z biblioteką niezgodną z używaną wersją programu MSVC i nie możesz uzyskać ani skompilować zgodnej wersji biblioteki, możesz użyć starszej wersji kompilatora do skompilowania projektu: Zmień właściwość zestawu **narzędzi platformy** dla projektu na wcześniejszy zestaw narzędzi. Aby uzyskać więcej informacji, zobacz [jak: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL`Wskazuje poziom zabezpieczeń i funkcji debugowania włączonych w standardowej bibliotece języka C++. Te funkcje mogą zmieniać reprezentację niektórych standardowych obiektów biblioteki C++, a tym samym je niezgodne z tymi, które używają różnych funkcji zabezpieczeń i debugowania. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary`Wskazuje wersję standardowej biblioteki języka C++ i środowiska uruchomieniowego C, która jest używana przez aplikację lub bibliotekę. Kod korzystający z jednej wersji standardowej biblioteki C++ lub środowiska uruchomieniowego C jest niezgodny z kodem, który używa innej wersji. Aby uzyskać więcej informacji, zobacz [/MD,/MT,/LD (Korzystanie z biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT`Wskazuje, że kod, który używa [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) jest połączony z obiektami skompilowanymi przy użyciu innego ustawienia dla opcji kompilatora [/zw](../../build/reference/zw-windows-runtime-compilation.md) . (**/Zw** obsługuje C++/CX.) Kod, który używa lub zależy od PPL, musi być skompilowany przy użyciu tego samego ustawienia **/zw** , które jest używane w pozostałej części aplikacji.

Upewnij się, że wartości tych symboli są spójne w projektach w rozwiązaniu programu Visual Studio, a także że są one spójne z kodem i bibliotekami, z którymi łączy się aplikacja.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteką innych firm i vcpkg

Jeśli ten błąd jest wyświetlany podczas próby skonfigurowania biblioteki innej firmy jako części kompilacji, należy rozważyć użycie [vcpkg](../../vcpkg.md), Menedżera pakietów języka C++, aby zainstalować i skompilować bibliotekę. Program vcpkg obsługuje dużą i rosnącą [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports), a także ustawia wszystkie właściwości konfiguracji i zależności wymagane dla zakończonych powodzeniem kompilacji w ramach projektu.

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
