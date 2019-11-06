---
title: Problemy przy migracji liczb zmiennoprzecinkowych
ms.date: 05/17/2017
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
ms.openlocfilehash: 0a84b764d395063f38cae299cff75437318b024e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626976"
---
# <a name="floating-point-migration-issues"></a>Problemy przy migracji liczb zmiennoprzecinkowych

Czasami gdy uaktualniasz projekty do nowszej wersji programu Visual Studio, może się okazać, że wyniki niektórych operacji zmiennoprzecinkowych uległy zmianie. Zwykle zdarza się to z jednego z dwóch powodów: zmiany generacji kodu, które wykorzystują lepsze wykorzystanie dostępnego procesora, oraz poprawki lub zmiany do algorytmów używanych w funkcjach matematycznych w bibliotece środowiska uruchomieniowego języka C (CRT). Ogólnie rzecz biorąc, nowe wyniki są poprawne w granicach określonych przez Standard języka. Przeczytaj, aby dowiedzieć się, co zostało zmienione, a jeśli jest to ważne, jak uzyskać te same wyniki, które zostały wcześniej wykonane przez funkcje.

## <a name="new-math-functions-and-universal-crt-changes"></a>Nowe funkcje matematyczne i uniwersalne zmiany CRT

Większość funkcji matematycznych w języku CRT jest dostępnych w programie Visual Studio przez lata, ale począwszy od Visual Studio 2013, uwzględniane są wszystkie funkcje wymagane przez C99 ISO. Te funkcje są implementowane w celu zrównoważenia wydajności z korekcją. Ponieważ generowanie prawidłowo zaokrąglonego wyniku w każdym przypadku może być niezwykle kosztowne, te funkcje są zaprojektowane w celu wydajnego tworzenia zbliżonego do poprawnego zaokrąglonego wyniku. W większości przypadków wynik wynoszący mieści się w jednostkach +/-1 jednostki o największej precyzji lub *ULP*w wyniku prawidłowo zaokrąglonego, chociaż mogą wystąpić sytuacje, w których występuje większa niedokładność. Jeśli używasz innej biblioteki matematycznej do uzyskiwania tych funkcji przed, różnice implementacji mogą być odpowiedzialne za zmianę w wynikach.

Gdy funkcje matematyczne zostały przeniesione do uniwersalnej CRT w programie Visual Studio 2015, zostały użyte niektóre nowe algorytmy, a niektóre usterki w implementacji funkcji, które były nowe w Visual Studio 2013 zostały naprawione. Te zmiany mogą prowadzić do wykrywalnych różnic w wynikach obliczeń zmiennoprzecinkowych korzystających z tych funkcji. Funkcje, które wystąpiły problemy z usterką, to ERF, exp2 —, reszta, remquo —, scalbln i scalbn —, a ich zmiennoprzecinkowe i długie podwójne odmiany.  Inne zmiany w programie Visual Studio 2015 Rozwiązano problemy z zachowaniem stanu zmiennoprzecinkowego i informacji o stanie wyjątku w funkcjach _clear87, _clearfp, fegetenv, fesetenv i feholdexcept.

## <a name="processor-differences-and-compiler-flags"></a>Różnice między procesorami i flagi kompilatora

Wiele funkcji wielozmiennoprzecinkowych bibliotek matematycznych ma różne implementacje dla różnych architektur procesora. Na przykład 32-bitowa architektura x86 CRT może mieć inną implementację niż 64-bit x64 CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury procesora CPU. Najbardziej wydajna implementacja jest wybierana dynamicznie w czasie wykonywania w zależności od zestawów instrukcji obsługiwanych przez procesor CPU. Na przykład w 32-bitowej architekturze x86, niektóre funkcje mają implementację x87 i implementację SSE2. W przypadku uruchamiania na PROCESORze, który obsługuje SSE2, używana jest szybsza implementacja SSE2. W przypadku uruchamiania na PROCESORze, który nie obsługuje SSE2, używana jest wolniejsza implementacja x87. Ten proces może zostać wyświetlony podczas migrowania starego kodu, ponieważ domyślna opcja architektury kompilatora x86 została zmieniona na [/arch: SSE2](../build/reference/arch-x86.md) w programie Visual Studio 2012. Ponieważ różne implementacje funkcji biblioteki matematycznej mogą korzystać z różnych instrukcji procesora CPU i różnych algorytmów w celu wygenerowania ich wyników, funkcje mogą generować różne wyniki na różnych platformach. W większości przypadków wyniki znajdują się w przedziale od +/-1 ULP prawidłowo zaokrąglonego wyniku, ale rzeczywiste wyniki mogą się różnić w zależności od procesorów.

Ulepszenia poprawności generowania kodu w różnych trybach zmiennoprzecinkowych w programie Visual Studio mogą również wpływać na wyniki operacji zmiennoprzecinkowych, gdy stary kod jest porównywany z nowym kodem, nawet w przypadku używania tych samych flag kompilatora. Na przykład kod wygenerowany przez program Visual Studio 2010, gdy [/FP: precyzyjne](../build/reference/fp-specify-floating-point-behavior.md) (wartość domyślna) lub `/fp:strict` został określony, może nie mieć propagowanych wartości pośrednich nieliczbowych (NaN) za pośrednictwem wyrażeń. W związku z tym niektóre wyrażenia, które spowodowały wynik liczbowy w starszych kompilatorach, mogą teraz prawidłowo generować wynik NaN. Możesz również zobaczyć różnice, ponieważ optymalizacje kodu włączone dla `/fp:fast` teraz korzystają z większej liczby funkcji procesora. Optymalizacje mogą korzystać z mniej instrukcji, ale mogą mieć wpływ na wygenerowane wyniki, ponieważ niektóre poprzednio widoczne operacje pośrednie zostały usunięte.

## <a name="how-to-get-identical-results"></a>Jak uzyskać identyczne wyniki

W większości przypadków zmiany zmiennoprzecinkowe w najnowszych kompilatorach i bibliotekach spowodują szybsze lub bardziej prawidłowe działanie lub oba te elementy. Jeśli instrukcje SSE2 zastępują instrukcje x87, możesz nawet zobaczyć lepszą wydajność mocy procesora. Jednakże jeśli masz kod, który musi dokładnie replikować zachowanie zmiennoprzecinkowe starszego kompilatora, rozważ użycie natywnych możliwości wielowymiarowych programu Visual Studio, a następnie Skompiluj odnośny projekt przy użyciu starszego zestawu narzędzi. Aby uzyskać więcej informacji, zobacz [Używanie natywnego wielu elementów docelowych w programie Visual Studio do kompilowania starych projektów](use-native-multi-targeting.md).

## <a name="see-also"></a>Zobacz także

[Uaktualnianie projektów ze starszych wersji wizualizacjiC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)