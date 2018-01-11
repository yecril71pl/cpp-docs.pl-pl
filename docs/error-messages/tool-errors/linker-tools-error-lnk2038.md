---
title: "Błąd narzędzi konsolidatora LNK2038 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 12/15/2017
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2038
dev_langs: C++
helpviewer_keywords: LNK2038
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13f65f403cac43551b787abab15713fb9ffab618
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2038"></a>Błąd narzędzi konsolidatora LNK2038

> Wykryto niezgodność dla "*nazwa*": wartość "*value_1*"nie odpowiada wartości"*value_2*" w *filename.obj*

Niezgodność symbol został wykryty przez konsolidator. Ten błąd wskazuje, że różne części aplikacji, w tym biblioteki lub innego obiektu kodu, czy łącza aplikacji, użyj definicje powodujące konflikt symbolu. [Wykrycia niezgodności](../../preprocessor/detect-mismatch.md) pragma służy do definiowania takie symbole i wykrywać ich wartości powodujące konflikt.

## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania

Ten błąd może wystąpić, gdy plik obiektu w projekcie jest przestarzały. Przed przystąpieniem do innych rozwiązań do tego błędu, należy wykonać czystą kompilację w celu zapewnienia aktualności plików obiektów.

Visual Studio definiuje następujące symbole, aby zapobiec łączenie niezgodne kodu, co może powodować błędy środowiska wykonawczego lub inne nieoczekiwane zachowania.

- `_MSC_VER`  
   Wskazuje, numery wersji głównej i pomocniczej kompilatora Visual C++, który jest używany do tworzenia aplikacji lub biblioteki. Kod, który ma być kompilowana przy użyciu jednej wersji kompilatora Visual C++ jest niezgodna z kodu, który ma być kompilowana przy użyciu wersji, który ma inną wersję główną i pomocniczą liczb. Aby uzyskać więcej informacji, zobacz `_MSC_VER` w [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

   Jeśli łączysz się do biblioteki, który nie jest zgodna z wersją kompilatora Visual C++, którego używasz, i nie można pobrać lub utworzyć zgodnej wersji biblioteki, aby skompilować projekt, można użyć starszej wersji kompilatora: Zmień <C1/>zestaw narzędzi platformy** właściwości projektu do wcześniejszych zestawu narzędzi. Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie platformy docelowej i zestawu narzędzi platformy](../../build/how-to-modify-the-target-framework-and-platform-toolset.md).

- `_ITERATOR_DEBUG_LEVEL`  
   Wskazuje poziom zabezpieczeń i debugowanie funkcji, które są włączone w standardowej bibliotece C++. Te funkcje można zmienić reprezentację określonych obiektów standardowa biblioteka C++ i tym samym były zgodne z tymi Użyj różnych zabezpieczenia i funkcji do debugowania. Aby uzyskać więcej informacji, zobacz [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md).

- `RuntimeLibrary`  
   Wskazuje wersję środowiska uruchomieniowego standardowa biblioteka C++ i C, używany przez aplikację lub biblioteki. Kod, który używa jednej wersji środowiska uruchomieniowego standardowa biblioteka C++ lub C jest niezgodny z kodu, który używa innej wersji. Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Użyj biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md).

- `_PPLTASKS_WITH_WINRT`  
   Wskazuje, że kod, który używa [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) jest połączone z obiektami skompilowana przy użyciu różne ustawienia dla [/ZW](../../build/reference/zw-windows-runtime-compilation.md) — opcja kompilatora. (**/ZW** obsługuje C + +/ CX.) Kod, który używa lub zależy od PPL muszą być skompilowane przy użyciu takie same **/ZW** ustawienie, który jest używany w pozostałej części aplikacji.

Upewnij się, że wartości tych symboli są spójne w całym projektów w rozwiązaniu programu Visual Studio i są one zgodne z kodem i bibliotek, które aplikacja łączy się.

## <a name="third-party-library-issues-and-vcpkg"></a>Problemy z biblioteki innych firm i Vcpkg

Jeśli zostanie wyświetlony ten błąd, gdy chcesz skonfigurować bibliotekę innych firm w ramach systemu, należy rozważyć użycie [Vcpkg](../../vcpkg.md), Visual C++ Menedżera pakietów, aby zainstalować i tworzenie biblioteki. Vcpkg obsługuje duży i rosnącym [listy bibliotek innych firm](https://github.com/Microsoft/vcpkg/tree/master/ports)i ustawia właściwości konfiguracji i zależności wymagane dla pomyślnej kompilacji w ramach projektu. Aby uzyskać więcej informacji, zobacz pokrewne [Visual C++ blogu](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) post.

## <a name="see-also"></a>Zobacz także

[Błędy i ostrzeżenia narzędzi konsolidatora](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)