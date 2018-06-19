---
title: Problemy przy migracji zmiennoprzecinkowe | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 0e6578486ada758482b270cd5505338e2acf3eb9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841905"
---
# <a name="floating-point-migration-issues"></a>Problemy przy migracji liczb zmiennoprzecinkowych  
  
Czasami po uaktualnieniu projektów do nowszej wersji programu Visual Studio, może się okazać zmieniono wyniki niektórych operacji zmiennoprzecinkowej. Zazwyczaj dzieje się z jednego z dwóch powodów: generowanie kodu zmienia lepsze wykorzystują dostępne procesora i usterki poprawki lub zmiany w algorytmów używanych w funkcji matematycznych w bibliotece C runtime (CRT). Ogólnie rzecz biorąc nowe wyniki są poprawne się w granicach określonego przez standard języka. Jak uzyskać takie same wyniki funkcji odczytu się dowiedzieć, co zostało zmienione, a jeśli ważne jest, otrzymano przed.  

## <a name="new-math-functions-and-universal-crt-changes"></a>Funkcje matematyczne nowy i zmiany Universal CRT  
  
Funkcje matematyczne CRT większości były dostępne w programie Visual Studio lat, ale począwszy od programu Visual Studio 2013, wszystkie funkcje wymagane przez ISO C99 są uwzględniane. Te funkcje są wdrażane do zrównoważenia wydajności z poprawności. Ponieważ produkujących poprawnie zaokrąglony wynik w każdym przypadku może być zbyt duży, te funkcje są przeznaczone do wydajnie tworzyć Zamknij zbliżenia się poprawnie zaokrąglony wynik. W większości przypadków wyniku zwracany znajduje się w +/-1 jednostka dokładności co najmniej lub *ulp*, poprawnie zaokrąglony wyniku, jednak może się zdarzyć, jeśli większej dokładności. Zostały korzystania z biblioteki matematyczne różnych uzyskać te funkcje przed różnice wdrożenia może być odpowiedzialne za zmiany w wynikach.   
    
Gdy funkcje matematyczne zostały przeniesione do Universal CRT w programie Visual Studio 2015, niektóre nowe algorytmy zostały użyte i Naprawiono kilka błędów w implementacji funkcji, które były nowe w programie Visual Studio 2013. Te zmiany mogą prowadzić do wykrywalny różnice wyników obliczeń zmiennoprzecinkowych, korzystających z tych funkcji. Funkcje, które ma problemy z usterki zostały erf, exp2 —, pozostałej, remquo —, scalbln oraz scalbn — i ich float i wariantów podwójnej długości.  Inne zmiany w programie Visual Studio 2015 naprawić problemy w zachowaniu przestawne word i wyjątków stanu informacji o stanie punktu w funkcjach _clear87 —, _clearfp — fegetenv, fesetenv i feholdexcept.  
  
## <a name="processor-differences-and-compiler-flags"></a>Różnice procesora i flagi kompilatora  
  
Liczby zmiennoprzecinkowe punktu funkcje biblioteki matematyczne mają różne implementacje dla innej architektury Procesora. Na przykład x86 32-bitowych CRT może mieć inną implementację niż x64 64-bitowych CRT. Ponadto niektóre funkcje mogą mieć wiele implementacji dla danej architektury Procesora. Najbardziej efektywne implementacji wybrano dynamicznie w czasie wykonywania w zależności od zbiór instrukcji obsługiwane przez procesor CPU. Na przykład w 32-bitowych x86 CRT, niektóre funkcje mają zarówno x87 implementacji i implementację SSE2. Podczas uruchamiania na procesora CPU obsługującego usługę SSE2, szybsze implementacji SSE2 jest używany. Podczas uruchamiania na Procesorze, który nie obsługuje SSE2, wolniejsze x87 implementacji jest używana. Błędy mogą wystąpić podczas migracji stary kodu, ponieważ opcją domyślną x86 kompilatora architektura zmieniony na [SSE2](../build/reference/arch-x86.md) w programie Visual Studio 2012. Ponieważ różnych implementacji funkcji biblioteki matematyczne mogą używać różnych instrukcji procesora CPU i różnych algorytmów w celu uzyskania ich wyników, funkcje może dać wyniki różne na różnych platformach. W większości przypadków wyniki są w +/-1 ulp poprawnie zaokrąglony wyniku, ale na rzeczywistą wydajność może się różnić we wszystkich procesorach.  
  
Ulepszenia poprawności generowanie kodu w różnych trybach w punkcie przestawne w programie Visual Studio również mogą wpłynąć na wyniki operacji zmiennoprzecinkowej, gdy poprzedni kod jest porównywany nowy kod, nawet w przypadku używania tego samego flagi kompilatora. Na przykład kod wygenerowany przez program Visual Studio 2010 po [/FP: dokładne](../build/reference/fp-specify-floating-point-behavior.md) (ustawienie domyślne) lub **/FP: strict** określono nie zostaną rozpropagowane wartości pośrednie nie liczby (NaN) za pomocą wyrażenia poprawnie. W związku z tym niektóre wyrażeń, które nadać wyniku numerycznego w starszych kompilatory, teraz może prawidłowo utworzenia wyniku NaN. Może również zostać wyświetlony różnice ponieważ optymalizacje kodu jest włączone dla **Fast** teraz korzystać z większą liczbą funkcji procesora. Te optymalizacje można używać instrukcji mniej, ale może mieć wpływ na wyniki wygenerowanego ponieważ niektóre widoczne wcześniej operacje pośrednie zostały usunięte.  
  
## <a name="how-to-get-identical-results"></a>Jak uzyskać identycznych wyników  
  
W większości przypadków zmiennoprzecinkowe zmian w najnowszej kompilatory i bibliotek powoduje szybsze i bardziej poprawne zachowanie lub oba. Może nawet lepszą wydajność mocy procesora podczas wyświetlane instrukcje SSE2 Zastąp x87 instrukcje. Jednak jeśli masz kod, który musi dokładnie replikować wartość zmiennoprzecinkowa punktu zachowanie starszego kompilatora, należy wziąć pod uwagę przy użyciu natywnych możliwości wielowersyjności kodu programu Visual Studio i skompiluj projekt dotyczy z starsze zestawu narzędzi. Aby uzyskać więcej informacji, zobacz [Użyj natywnego wielowersyjności kodu w programie Visual Studio do kompilacji projektów starego](use-native-multi-targeting.md).  
  
## <a name="see-also"></a>Zobacz także  
  
[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)  
