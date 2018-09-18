---
title: Błąd narzędzi konsolidatora LNK2038 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2038
dev_langs:
- C++
helpviewer_keywords:
- LNK2038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 009644f18068454b0c765118b29c009cd33241a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118118"
---
# <a name="linker-tools-error-lnk2038"></a>Błąd narzędzi konsolidatora LNK2038

> Wykryto niezgodność "*nazwa*": wartość "*value_1*"nie jest zgodna wartość"*value_2*" w *filename.obj*

Niezgodność symboli została wykryta przez konsolidator. Ten błąd wskazuje, że różne części aplikacji, takimi jak biblioteki lub innych obiektów kodu czy połączeń aplikacji, używają sprzecznych definicji symbolu. [Wykrycia niezgodności](../../preprocessor/detect-mismatch.md) pragmy jest używane do definiowania takich symboli i wykrywanie ich wartości powodujących konflikt.

## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i potencjalne rozwiązania

Ten błąd może wystąpić, gdy plik obiektu w projekcie jest nieaktualny. Zanim spróbujesz innych rozwiązań tego błędu, należy wykonać czystą kompilację, aby upewnić się, że pliki obiektów są aktualne.

Program Visual Studio definiuje następujące symbole, aby zapobiec łączeniu niezgodnego kodu, który może spowodować błędy czasu wykonywania lub inne nieoczekiwane zachowania.

- `_MSC_VER` Wskazuje numery wersji głównych i pomocniczych kompilatora języka Visual C++, który jest używany do tworzenia aplikacji lub biblioteki. Kod, który jest kompilowany przy użyciu jednej wersji kompilatora Visual C++ jest niezgodny z kodem, który jest kompilowany przy użyciu wersji zawierającej różnych głównych i pomocniczych numerów wersji. Aby uzyskać więcej informacji, zobacz `_MSC_VER` w [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

   Jeśli łączysz się do biblioteki, który nie jest zgodna z wersją kompilatora Visual C++, którego używasz, i nie można pobrać lub utworzyć zgodnej wersji biblioteki, aby skompilować projekt, można użyć starszej wersji kompilatora: Zmień **zestaw narzędzi platformy** właściwości projektu do wcześniejszych zestawu narzędzi. Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL` Wskazuje poziom zabezpieczeń i funkcje debugujące, które są włączone w standardowej biblioteki języka C++. Te funkcje mogą zmienić reprezentację niektórych obiektów standardowej biblioteki języka C++ i tym samym są zgodne z tymi, które używają różnych zabezpieczeń i funkcji do debugowania. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary` Wskazuje wersję środowiska wykonawczego standardowej biblioteki języka C++ i C, który jest używany przez aplikację lub bibliotekę. Kod, który używa jednej wersji środowiska wykonawczego standardowej biblioteki języka C++ lub C jest niezgodny z kodem, który korzysta z innej wersji. Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Korzystaj z bibliotek wykonawczych)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT` Wskazuje, że kod, który używa [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) jest połączony z obiektami skompilowanymi przy użyciu różnych ustawienie [/ZW](../../build/reference/zw-windows-runtime-compilation.md) — opcja kompilatora. (**/ZW** obsługuje C + +/ CX.) Kod, który używa lub zależy od PPL, muszą być skompilowane, korzystając z tych samych **/ZW** ustawienia, która jest używana w pozostałej części aplikacji.

Upewnij się, że wartości tych symboli są spójne dla projektów w rozwiązaniu programu Visual Studio i są one zgodne z kodem i bibliotekami, które łączą się aplikacje.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteki innych firm i Vcpkg

Jeśli zostanie wyświetlony ten błąd, jeśli próbujesz skonfigurować biblioteki innych firm w ramach kompilacji, należy rozważyć użycie [Vcpkg](../../vcpkg.md), do Visual C++ Menedżera pakietów, instalowanie i tworzenie biblioteki. Vcpkg obsługująca duży i rosnący [listę bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports)i ustawia właściwości konfiguracji i zależności wymagane do pomyślnej kompilacji w ramach projektu. Aby uzyskać więcej informacji, zobacz powiązane [blogu Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) wpis.

## <a name="see-also"></a>Zobacz także

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)