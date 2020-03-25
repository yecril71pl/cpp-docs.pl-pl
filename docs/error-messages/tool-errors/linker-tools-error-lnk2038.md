---
title: Błąd narzędzi konsolidatora LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 45078d8e1bdbeb23dd311d915ba2cf47e42b2663
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194515"
---
# <a name="linker-tools-error-lnk2038"></a>Błąd narzędzi konsolidatora LNK2038

> wykryto niezgodność dla elementu "*name*": wartość "*value_1*" nie jest zgodna z wartością "*value_2*" w *pliku filename. obj*

Program łączący wykrył niezgodność symboli. Ten błąd wskazuje, że różne części aplikacji, w tym biblioteki lub inny kod obiektu, z którym łączy się aplikacja, używają definicji w konflikcie symboli. Dyrektywa pragma [wykrywania niezgodności](../../preprocessor/detect-mismatch.md) służy do definiowania takich symboli i wykrywania ich wartości powodujących konflikt.

## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania

Ten błąd może wystąpić, gdy plik obiektu w projekcie jest nieaktualny. Przed podjęciem próby wykonania innych rozwiązań tego błędu Wykonaj czystą kompilację, aby upewnić się, że pliki obiektów są aktualne.

Program Visual Studio definiuje następujące symbole, aby zapobiec łączeniu niezgodnego kodu, co może spowodować błędy w czasie wykonywania lub inne nieoczekiwane zachowanie.

- `_MSC_VER` wskazuje główne i pomocnicze numery wersji kompilatora firmy Microsoft C++ (MSVC), które są używane do kompilowania aplikacji lub biblioteki. Kod kompilowany przy użyciu jednej wersji MSVC jest niezgodny z kodem, który jest kompilowany przy użyciu wersji, która ma inne główne i pomocnicze numery wersji. Aby uzyskać więcej informacji, zobacz `_MSC_VER` w [wstępnie zdefiniowanych makrach](../../preprocessor/predefined-macros.md).

   Jeśli łączysz się z biblioteką niezgodną z używaną wersją programu MSVC i nie możesz uzyskać ani skompilować zgodnej wersji biblioteki, możesz użyć starszej wersji kompilatora do skompilowania projektu: Zmień właściwość zestawu **narzędzi platformy** dla projektu na wcześniejszy zestaw narzędzi. Aby uzyskać więcej informacji, zobacz [jak: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` wskazuje poziom zabezpieczeń i funkcji debugowania, które są włączone w C++ standardowej bibliotece. Te funkcje mogą zmieniać reprezentację niektórych C++ standardowych obiektów biblioteki, a tym samym sprawiać, że są one niezgodne z tymi, które używają różnych funkcji zabezpieczeń i debugowania. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` wskazuje wersję biblioteki C++ standardowej i środowiska uruchomieniowego języka C, która jest używana przez aplikację lub bibliotekę. Kod korzystający z jednej wersji biblioteki C++ standardowej lub środowiska uruchomieniowego języka C jest niezgodny z kodem, który używa innej wersji. Aby uzyskać więcej informacji, zobacz [/MD,/MT,/LD (Korzystanie z biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` wskazuje, że kod, który używa [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) jest połączony z obiektami skompilowanymi przy użyciu innego ustawienia dla opcji kompilatora [/zw](../../build/reference/zw-windows-runtime-compilation.md) . ( **/Zw** obsługuje C++/CX.) Kod, który używa lub zależy od PPL, musi być skompilowany przy użyciu tego samego ustawienia **/zw** , które jest używane w pozostałej części aplikacji.

Upewnij się, że wartości tych symboli są spójne w projektach w rozwiązaniu programu Visual Studio, a także że są one spójne z kodem i bibliotekami, z którymi łączy się aplikacja.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteką innych firm i Vcpkg

Jeśli ten błąd jest wyświetlany podczas próby skonfigurowania biblioteki innej firmy jako części kompilacji, należy rozważyć użycie [Vcpkg](../../vcpkg.md), Menedżera pakietów Visual C++ Package, aby zainstalować i skompilować bibliotekę. Program Vcpkg obsługuje dużą i rosnącą [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports), a także ustawia wszystkie właściwości konfiguracji i zależności wymagane dla zakończonych powodzeniem kompilacji w ramach projektu. Aby uzyskać więcej informacji, zobacz odpowiedni wpis w [blogu wizualnym C++ ](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) .

## <a name="see-also"></a>Zobacz też

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
