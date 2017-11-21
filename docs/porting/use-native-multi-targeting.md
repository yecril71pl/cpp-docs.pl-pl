---
title: "Użyj natywnego wielowersyjności kodu w programie Visual Studio do kompilacji projektów starego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- C++ native multi-targeting
- upgrading Visual C++ applications, retargeting
ms.assetid: b115aabe-a9dc-4525-90d3-367d97ea20c9
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5475a211e3b0c116a7ab51cb7b7b128f5742e0cc
ms.sourcegitcommit: c9108f0c45b7a634d4e6e5c2d2ec192d50ffdbab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="use-native-multi-targeting-in-visual-studio-to-build-old-projects"></a>Użyj natywnego wielowersyjności kodu w programie Visual Studio do kompilacji projektów starego

Zaleca się normalnie, aktualizowanie projektów podczas instalowania najnowszej wersji programu Visual Studio. Aktualizowanie projektów i kod koszt jest zazwyczaj więcej niż przesunięcie przez zalet nowego środowiska IDE, kompilator, biblioteki i narzędzia. Wiemy, że nie można zaktualizować niektórych projektów. Masz pliki binarne, które są powiązane z starsza bibliotek i platform, że przyczyn konserwacji nie można uaktualnić. Kod może używać konstrukcji języka niestandardowych, które spowoduje przerwanie, jeśli został on przeniesiony do nowszej kompilatora. Kod może polegać na 3 bibliotek strona skompilowanego dla określonej wersji programu Visual C++. Lub może powodować biblioteki dla innych osób, które muszą wskazywać określonej starszej wersji programu Visual C++.

Na szczęście można użyć programu Visual Studio 2017 i programu Visual Studio 2015 do kompilacji projektów tego docelowego starsze procesami kompilatora i bibliotek. Uaktualnienie programu Visual Studio 2010, Visual Studio 2012, Visual Studio 2013 lub projektu programu Visual Studio 2015 mógł korzystać z nowych funkcji w środowisku IDE nie jest konieczne:

 - Nowe funkcje refaktoryzacji C++ i eksperymentalną edytora
 - Nowe narzędzia diagnostyczne debugera okno i w oknie Lista błędów
 - Revamped punktów przerwania, wyjątki okna i nowych wskazówek
 - Nowe narzędzia nawigacji i wyszukiwanie kodu
 - Nowe poprawki szybkie C++ i rozszerzenia narzędzi wydajności.

Możesz też określić projektów programu Visual Studio 2008, ale nie można używać bez zmian. Aby uzyskać więcej informacji zapoznaj się z instrukcjami w sekcji Visual Studio 2008.

Najnowsze wersje programu Visual Studio obsługują macierzysty multi-targeting i dwustronną komunikację projektów. Natywny multi-targeting jest możliwość kompilować przy użyciu procesami zainstalowanych przez poprzednie wersje programu Visual Studio IDE najnowsze. Dwustronną komunikację jest możliwość ładowania projektów utworzonych za pomocą poprzedniej wersji IDE bez wprowadzania żadnych zmian w projekcie najnowsze IDE. Po zainstalowaniu najnowszej wersji programu Visual Studio side-by-side z istniejącej wersji, do tworzenia projektów za pomocą nowej wersji środowiska IDE z kompilatora i narzędzi z istniejącej wersji programu. Innych członków zespołu można nadal używać projektów w starszej wersji programu Visual Studio.

Użyj starszych zestawu narzędzi, można wykonać korzystać wielu z najnowszych funkcji IDE, ale nie najnowszych rozwiązań narzędzia kompilatora i bibliotek kompilacji C++. Na przykład nie będzie można używać nowych ulepszeń zgodność języka nowych debugowania i funkcji analizy kodu lub pobrania zwiększyć przepustowość kompilacji najnowszego zestawu narzędzi. Dostępne są także niektóre funkcje IDE, które są niezgodne z procesami starszej. Na przykład typ może brakować informacji w pamięci profilera, a operacja refaktoryzacji **Konwertuj na nieprzetworzony ciąg literały** generuje C ++ 11 zgodne kod, który nie będzie skompilować, korzystając z programu Visual Studio 2012 lub starszy procesami.

## <a name="how-to-use-native-multi-targeting-in-visual-studio"></a>Jak używać natywnego wielowersyjności kodu w programie Visual Studio

Po zainstalowaniu programu Visual Studio side-by-side z wersją starszą, otwórz istniejący projekt w nowej wersji programu Visual Studio. Po załadowaniu projektu programu Visual Studio zapyta, czy chcesz uaktualnić go do korzystania z najnowszych kompilatora C++ i bibliotek. Ponieważ projektu, aby zachować starsze kompilator i biblioteki należy wybrać **anulować** przycisku.

Program Visual Studio jest trwały dotyczących uaktualniania projektu. Aby uniknąć wyświetlania okno dialogowe uaktualniania za każdym razem, gdy załadowanie projektu, można zdefiniować następującą właściwość w projektach, lub w plikach .props lub .targets ich importowania:

`<VCProjectUpgraderObjectName>NoUpgrade</VCProjectUpgraderObjectName>`

Należy usunąć tę właściwość, jeśli chcesz uaktualnić swoje projekty.

Jeśli wybierzesz nie uaktualnić program Visual Studio nie zmienia plików rozwiązania lub projektu. Podczas kompilowania projektu wygenerowanych plików binarnych są w pełni zgodne z tymi, które zostały utworzone w starszej wersji programu Visual Studio. Jest to spowodowane Visual Studio korzysta z tej samej kompilatora C++ i łączy tej samej biblioteki środowiskiem IDE starsze dostarczonych z programem. Jest to Dlaczego okno dialogowe uaktualniania wyświetli ostrzeżenie, aby zachować starszej wersji programu Visual Studio zainstalowany, wybranie opcji **anulować**.

## <a name="instructions-for-visual-studio-2008"></a>Instrukcje dotyczące programu Visual Studio 2008  
  
Program Visual Studio 2008 oferowały własny system kompilacji dedykowanych wywołuje program VCBuild w języku C++. Począwszy od programu Visual Studio 2010, projektów Visual C++ zostały zmienione na Użyj programu MSBuild. Oznacza to, że musi przejść do kroku aktualizacji do tworzenia projektów programu Visual Studio 2008 w najnowszej wersji programu Visual Studio. Zaktualizowano projekt nadal generuje pliki binarne, które są w pełni zgodne z dane binarne utworzone za pomocą programu Visual Studio 2008 IDE.

Najpierw oprócz bieżącej wersji programu Visual Studio oraz programu Visual Studio 2010 należy zainstalować na tym samym komputerze co program Visual Studio 2008. Tylko program Visual Studio 2010 instaluje skrypty programu MSBuild, które są wymagane do projektów programu Visual Studio 2008. 

Następnie należy zaktualizować program Visual Studio 2008 rozwiązanie i projekty do bieżącej wersji programu Visual Studio. Zaleca się utworzenie kopii zapasowej projektów i rozwiązań plików przed uaktualnieniem. Aby rozpocząć proces uaktualniania, otwórz rozwiązanie w bieżącej wersji programu Visual Studio. Gdy pojawi się monit uaktualniania, zapoznaj się z informacjami, a następnie wybierz **OK** uruchomiony w celu uaktualnienia. Jeśli masz więcej niż jednego projektu w rozwiązaniu, należy zaktualizować Kreator utworzy nowy .vcxproj projektu plików side-by-side z istniejącymi plikami .vcproj. Tak długo, jak również istnieje kopia oryginalnego pliku SLN, uaktualnienie nie ma innych wpływu na istniejących projektów programu Visual Studio 2008.

Po zakończeniu uaktualniania, jeśli raport dziennika zawiera błędy lub ostrzeżenia dla żadnego z projektów, ich należy dokładnie przejrzeć. Konwersja z program VCBuild MSBuild mogą powodować problemy. Upewnij się, poznanie i wdrożenie wszystkie elementy akcji wymienionych w raporcie. Aby uzyskać więcej informacji na raport dziennika uaktualniania i problemów, które mogą występować podczas konwertowania program VCBuild dla programu MSBuild, zobacz [C++ natywnego Wielowersyjności](https://blogs.msdn.microsoft.com/vcblog/2009/12/08/c-native-multi-targeting/) wpis w blogu.

Po zakończeniu uaktualniania projektu i rozwiązaniu problemów w pliku dziennika, rozwiązania faktycznie dotyczy najnowszego zestawu narzędzi. Ostatni krok Zmień właściwości dla każdego projektu w rozwiązaniu do używania narzędzi Visual Studio 2008. Z rozwiązaniem załadowany w bieżącej wersji programu Visual Studio dla każdego projektu w rozwiązaniu, otwórz projekt **strony właściwości** okno dialogowe: kliknij prawym przyciskiem myszy projekt w **Eksploratora rozwiązań** , a następnie Wybierz **właściwości**. W **strony właściwości** okno dialogowe, zmień **konfiguracji** wartość z listy rozwijanej do **wszystkie konfiguracje**. W **właściwości konfiguracji**, wybierz pozycję **ogólne**, a następnie zmień **zestaw narzędzi platformy** do **programu Visual Studio 2008 (v90)**.

Po tej zmianie program Visual Studio 2008 kompilator i biblioteki są używane do generowania dane binarne projektu podczas kompilowania rozwiązania w bieżącej wersji programu Visual Studio.

## <a name="install-an-older-visual-studio-toolset"></a>Zainstaluj starszą narzędzi Visual Studio

Masz stary projekt Visual C++, która nie może lub nie chcesz uaktualnić, ale nie wersji narzędzi platformy odpowiadającego projektu. W takim przypadku można pobrać zestawu narzędzi, można zainstalować wolnego Visual Studio Community lub wersji Express edition w wersji, które są potrzebne. Każda wersja programu Visual Studio z programu Visual Studio 2008 na można zainstalować kompilator, narzędzia i biblioteki należy określić tej wersji z bieżącego programu Visual Studio. Wyszukiwanie Microsoft Download Center, aby znaleźć i pobrać określonej wersji programu Visual Studio. Upewnij się, że wybrane opcje instalacji C++ podczas instalacji. Po zakończeniu instalacji uruchom danej wersji programu Visual Studio, aby zainstalować wszystkie aktualizacje. Wyszukaj także wszelkie zmiany aktualizacji systemu Windows, które mogą być wymagane. Ten proces sprawdzania aktualizacji może być konieczne powtórzyć więcej niż raz, aby pobrać każdej aktualizacji.

Oto niektóre pliki programu Visual Studio, które może być konieczne:

  - [Microsoft Visual Studio Community 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48146)  
  - [Microsoft Visual Studio Express 2013 for Windows Desktop z aktualizacją 5](https://www.microsoft.com/en-us/download/details.aspx?id=48131)  
  - [Microsoft Visual Studio Express 2012 for Windows Desktop](https://www.microsoft.com/en-us/download/details.aspx?id=34673)  
  - [Visual Studio 2012 Update 5](https://www.microsoft.com/en-us/download/details.aspx?id=34673)  
  - [Microsoft Visual C++ 2010 Express (Instalator sieci Web)](https://download.microsoft.com/download/1/D/9/1D9A6C0E-FC89-43EE-9658-B9F0E3A76983/vc_web.exe)  
  - [Dodatek Service Pack 1 dla programu Microsoft Visual Studio 2010](https://www.microsoft.com/en-us/download/details.aspx?id=23691)  
  - [Microsoft Visual C++ 2008 Express z dodatkiem SP1 (Instalator sieci Web)](https://go.microsoft.com/?linkid=7729279)  

Po zainstalowaniu tych produktów **zestaw narzędzi platformy** właściwości listy rozwijanej w **strony właściwości** okno dialogowe jest automatycznie aktualizowany, aby wyświetlić dostępne procesami. Można teraz używać najnowszej wersji programu Visual Studio do tworzenia projektów dla tych starsze wersje zestawu narzędzi bez konwersji lub jej uaktualnienie.

## <a name="see-also"></a>Zobacz też

[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Ulepszenia zgodność języka C++ w programie Visual Studio 2017 r.](../cpp-conformance-improvements-2017.md)  
