---
title: Problemy dotyczące migracji liczb zmiennoprzecinkowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36a1b552-2f2b-4919-bc9d-c17f42434954
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e204e8dcc0d846294393edf9bf73b86360b40de2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421989"
---
# <a name="floating-point-migration-issues"></a>Problemy dotyczące migracji liczb zmiennoprzecinkowych  

  
Czasami podczas uaktualniania projektów do nowszej wersji programu Visual Studio, może się okazać, że wyniki niektórych operacji zmiennoprzecinkowych zostały zmienione. Zwykle dzieje się z jednego z dwóch powodów: generowanie kodu zmienia tego lepiej korzystać z dostępnego procesora i usterki poprawki lub zmiany algorytmów używanych w funkcje matematyczne w bibliotece środowiska uruchomieniowego języka C (CRT). Ogólnie rzecz biorąc nowe wyniki są zgodne w granicach określonego przez standard języka. Zapoznaj się z Dowiedz się, co zostało zmienione, a jeśli ważne jest, jak uzyskać te same wyniki funkcji stało się przed.  

## <a name="new-math-functions-and-universal-crt-changes"></a>Funkcje matematyczne nowy i zmiany Universal CRT  
  
Większość funkcji matematycznych CRT, były dostępne w programie Visual Studio przez wiele lat, ale począwszy od programu Visual Studio 2013, wszystkie funkcje wymagane przez ISO C99 zostały uwzględnione. Te funkcje są implementowane aby zrównoważyć wydajność za pomocą poprawności. Ponieważ tworzenie poprawnie zaokrąglony wynik w każdym przypadku może być zbyt duży, te funkcje są przeznaczone do wydajnego tworzenia bliskie zbliżenia wyniku poprawnie zaokrąglony. W większości przypadków wynik tworzony mieści się w +/-1 jednostka co najmniej dokładności lub *ulp*, prawidłowo zaokrąglone wyniku, chociaż może się zdarzyć, gdy większej dokładności. Jeśli biblioteki matematyczne różnych była używana, można pobrać te funkcje przed, różnic w implementacji może być odpowiedzialny za zmiany w wynikach.   
    
Gdy funkcje matematyczne zostały przeniesione do Universal CRT w programie Visual Studio 2015, niektóre z nowych algorytmów były używane i rozwiązano kilka błędów w celu wykonania funkcji, które były nowe w programie Visual Studio 2013. Te zmiany mogą powodować wykrywalny różnice wyników wykonywania obliczeń zmiennopozycyjnych, które używają tych funkcji. Funkcje, które miały problemów usterki były erf, exp2 —, pozostałą, remquo —, scalbln i scalbn — i ich float i wariantów typu long double.  Inne zmiany w programie Visual Studio 2015 Rozwiązano problemy zachowywanie przestawne programu word i wyjątków stanu informacji o stanie punktu _clear87 — _clearfp —, fegetenv, fesetenv i feholdexcept funkcji.  
  
## <a name="processor-differences-and-compiler-flags"></a>Różnice procesora i flagi kompilatora  
  
Liczby zmiennoprzecinkowej punktu funkcji bibliotek matematycznych mają różne implementacje dla innej architektury Procesora. Na przykład x86 32-bitowych CRT może mieć inną implementację od x64 64-bitowych CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury Procesora. Najbardziej efektywny sposób wdrażania jest wybierana dynamicznie w czasie wykonywania w zależności od zestawów instrukcji, obsługiwanych przez CPU. Na przykład w x86 32-bitowych CRT, niektóre funkcje mają zarówno x87 implementacji i implementację SSE2. Podczas uruchamiania, na którego procesor CPU obsługuje SSE2, szybsze implementacji SSE2 jest używany. Podczas uruchamiania na procesorze CPU, który nie obsługuje SSE2, wolniejsze x87 implementacja jest używana. Będzie to miało podczas migracji stary kod, ponieważ domyślny x86 kompilator architektury zmieniony na [SSE2](../build/reference/arch-x86.md) w programie Visual Studio 2012. Ponieważ różne implementacje funkcji bibliotek matematycznych może używać różne instrukcje procesora CPU i różnych algorytmów, aby wygenerować ich wyniki, funkcje mogą wygenerować różne wyniki na różnych platformach. W większości przypadków wyniki znajdują się w +/-1 ulp poprawnie zaokrąglone wyników, ale rzeczywiste wyniki mogą się różnić we wszystkich procesorach.  
  
Ulepszenia poprawność generowanie kodu w różnych trybach punktu zmiennoprzecinkowego, w programie Visual Studio może również wpływać na wyniki operacji zmiennoprzecinkowych gdy poprzedni kod jest porównywany z nowego kodu, nawet w przypadku używania tego samego flagi kompilatora. Na przykład, kod wygenerowany przez program Visual Studio 2010 podczas [/FP: precise](../build/reference/fp-specify-floating-point-behavior.md) (ustawienie domyślne) lub `/fp:strict` został określony może nie mieć propagowane wartości pośrednie nie a liczbą (NaN) za pomocą wyrażenia poprawnie. W efekcie niektóre wyrażenia, które udostępniła wynik liczbowy w starszych kompilatory mogą teraz poprawnie rezultatów NaN. Również może zostać wyświetlony różnic, ponieważ optymalizacje kodu jest włączone dla `/fp:fast` teraz korzystać z większą liczbą funkcji procesora. Optymalizacje te można użyć mniejszej liczby instrukcji, ale mogą mieć wpływ na wyniki wygenerowanego ponieważ niektóre wcześniej widoczne operacje pośrednie zostały usunięte.  
  
## <a name="how-to-get-identical-results"></a>Jak uzyskać takie same wyniki  
  
W większości przypadków zmiennoprzecinkowych zmian w najnowszych kompilatory i biblioteki powoduje zachowanie szybciej i bardziej poprawny i / lub. Może nawet zobaczysz lepszą wydajność moc procesora, gdy instrukcje SSE2 Zastąp x87 instrukcje. Jednak jeśli masz kod, który należy dokładnie replikować zmiennoprzecinkowego punktu zachowanie starszego kompilatora, należy wziąć pod uwagę przy użyciu możliwości natywnej wielowersyjności kodu programu Visual Studio i kompilowania projektu starszy zestaw narzędzi których to dotyczy. Aby uzyskać więcej informacji, zobacz [Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów](use-native-multi-targeting.md).  
  
## <a name="see-also"></a>Zobacz także  
  
[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)  