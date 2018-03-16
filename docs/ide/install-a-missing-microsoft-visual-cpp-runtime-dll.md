---
title: "Zainstaluj brakujące Microsoft Visual C++ Runtime biblioteki DLL | Dokumentacja firmy Microsoft"
description: "Jak znaleźć i zainstalować Brak biblioteki DLL środowiska uruchomieniowego Visual C++."
ms.date: 03/13/2018
ms.topic: article
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6410c9753577852989172121d01c9d768f5373b3
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="install-a-missing-microsoft-visual-c-runtime-dll"></a>Zainstaluj brakujące Microsoft Visual C++ Runtime biblioteki DLL

Programów napisanych przy użyciu programu Microsoft Visual C++ często wymagają niektóre dodatkowe pliki biblioteki środowiska uruchomieniowego Visual C++ lub biblioteki dll do uruchomienia. Te środowiska uruchomieniowego bibliotek DLL są dostępne w *pakietu redystrybucyjnego*, program Instalator plik biblioteki, dla każdej wersji programu Visual C++. Pakiet redystrybucyjny, wymagane przez dowolnego programu powinien znajdować się przez jego Instalatora. Jeśli nie jest dostępne, można czasami samodzielnie zainstaluj pakiet redystrybucyjny i usuń błąd systemu po uruchomieniu programu.

Można określić program brakuje środowiska uruchomieniowego Visual C++ DLL Jeśli błąd systemu podczas uruchamiania programu, który mówi, takie jak "programu nie można uruchomić, ponieważ VCRuntime140.dll brakuje z komputera". Często ten problem można naprawić odinstalować program, a następnie zainstalować ją ponownie. Zdecydowanie zaleca się najpierw w trakcie tego kroku przed inne potencjalne rozwiązanie.

Czasami pakietu redystrybucyjnego zainstalowane przez program jest nieaktualny. Firma Microsoft udostępnia zaktualizowanych wersji środowiska uruchomieniowego bibliotek DLL od czasu do czasu adres błędów i problemów z zabezpieczeniami. Aby zachować komputera z systemem bezpiecznie i poprawnie, jest dobrym pomysłem jest korzystanie z najnowszych aktualizacji dla dowolnego programu obsługi DLL. Sprawdź, czy jest zaktualizowany Instalator program, który może zapewnić tę aktualizację można. Jeśli istnieje, użyj zaktualizowany Instalator, aby ponownie zainstalować program.

Jeśli ponownie zainstalować program nie czyni to błąd systemowy zniknie, następnie Instalator programu może być uszkodzony lub uszkodzony lub biblioteki DLL środowiska uruchomieniowego na komputerze może być uszkodzony. Spróbuj pobrać nową kopię Instalatora programu i użyć go do ponownej instalacji pierwszej. Jeśli to nie zadziała, lub Instalator nie jest dostępna, następnie może być wyodrębnienie sprawdzanie Microsoft Visual C++ Redistributable instalacji na komputerze.

Ta tabela zawiera listę bibliotek DLL, które znajdują się w co najmniej jednego pakietu redystrybucyjnego, oraz linków, aby pobrać kopię pakietu redystrybucyjnego. Aby pobrać nową kopię pakietu redystrybucyjnego powinny być widoczne w przypadku istniejącej instalacji można naprawić.

|Brak biblioteki DLL  |Pakiet redystrybucyjny programu  |
|---------|---------|
|atl80.dll<br />msvcm80.dll<br />msvcp80.dll<br />msvcr80.dll<br />mfc80.dll<br />mfc80u.dll<br />mfcm80.dll<br />mfcm80u.dll|[Microsoft Visual C++ 2005 Redistributable (x86)](https://www.microsoft.com/en-us/download/details.aspx?id=5638)<br />[Pakiet redystrybucyjny Microsoft Visual C++ 2005 (x64)](https://www.microsoft.com/en-us/download/details.aspx?id=18471)<br />[Aktualizacja zabezpieczeń programu Microsoft Visual C++ 2005 z dodatkiem Service Pack 1 pakietu redystrybucyjnego MFC](https://www.microsoft.com/en-us/download/details.aspx?id=26347)|
|atl90.dll<br />msvcr90.dll<br />msvcm90.dll<br />msvcp90.dll<br />mfc90.dll<br />mfc90u.dll<br />mfcmifc80.dll<br />mfcm90.dll<br />mfcm90u.dll|[Microsoft Visual C++ 2008 Redistributable - x86](https://www.microsoft.com/en-us/download/details.aspx?id=5582)<br />[Microsoft Visual C++ 2008 Redistributable - x64](https://www.microsoft.com/en-us/download/details.aspx?id=2092)<br />[Aktualizacja zabezpieczeń programu Microsoft Visual C++ 2008 z dodatkiem Service Pack 1 pakietu redystrybucyjnego MFC](https://www.microsoft.com/en-us/download/details.aspx?id=26368)|
|atl100.dll<br />msvcr100.dll<br />msvcp100.dll<br />msdia71.dll<br />vcomp100.dll<br />mfc100.dll<br />mfc100u.dll<br />mfcmifc80.dll<br />mfcm100.dll<br />mfcm100u.dll|[Microsoft Visual C++ 2010 x86 pakietu redystrybucyjnego](https://www.microsoft.com/en-us/download/details.aspx?id=8328)<br />[Microsoft Visual C++ 2010 x64 pakietu redystrybucyjnego](https://www.microsoft.com/en-us/download/details.aspx?id=13523)<br />[Aktualizacja zabezpieczeń programu Microsoft Visual C++ 2010 z dodatkiem Service Pack 1 pakietu redystrybucyjnego MFC](https://www.microsoft.com/en-us/download/details.aspx?id=26999)|
|atl110.dll<br />msvcr110.dll<br />msvcp110.dll<br />mfc110.dll<br />mfc110u.dll<br />mfcmifc80.dll<br />mfcm110.dll<br />mfcm110u.dll<br />concrt110.dll<br />vccorlib110.dll<br />vcamp110.dll<br />vcomp110.dll|[Microsoft Visual C++ 2012 Redistributable (dla programu Visual Studio 2012 z aktualizacją 4)](https://www.microsoft.com/en-us/download/details.aspx?id=30679)|
|msvcr120.dll<br />msvcp120.dll<br />mfc120.dll<br />mfc120u.dll<br />mfcmifc80.dll<br />mfcm120.dll<br />mfcm120u.dll<br />concrt120.dll<br />vccorlib120.dll<br />vcamp120.dll<br />vcomp120.dll|[Microsoft Visual C++ 2013 Redistributable (łącza do poszczególnych pliki do pobrania)](https://support.microsoft.com/en-us/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package)<br />[Biblioteka MFC wielobajtowe dla programu Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770)<br />[2013 środowiska uruchomieniowego Visual C++ dla aplikacji ładowanych bezpośrednio Windows 8.1 (Pobierz zip)](http://download.microsoft.com/download/5/F/0/5F0F8404-9329-44A9-8176-ED6F7F746F25/VCLibs_Redist_Packages.zip)|
|vcruntime140.dll<br />vcruntime140_app.dll<br />msvcp140.dll<br />msvcp140_1.dll, etc.<br />mfc140.dll<br />mfc140u.dll<br />mfcmifc80.dll<br />mfcm140.dll<br />mfcm140u.dll<br />concrt140.dll<br />vccorlib140.dll<br />vcamp140.dll<br />vcomp140.dll|[Microsoft Visual C++ 2017 (x86) pakietu redystrybucyjnego](https://go.microsoft.com/fwlink/?LinkId=746571)<br />[Microsoft Visual C++ 2017 (x64) pakietu redystrybucyjnego](https://go.microsoft.com/fwlink/?LinkId=746572)|
|msvcr100_clr0400.dll<br />msvcr110_clr0400.dll<br />msvcr120_clr0400.dll|[Pobierz .NET Framework](https://www.microsoft.com/net/download/framework)|

### <a name="to-repair-an-existing-redistributable-package"></a>Aby naprawić istniejącego pakietu redystrybucyjnego

1. Otwórz Panel sterowania. W systemie Windows 10, wprowadź *Panelu sterowania* na pulpicie wyszukiwania sterowania na pasku zadań, a następnie wybierz **Panelu sterowania** z możliwości.

2. W Panelu sterowania, wybierz **programy** > **programy i funkcje**. Wybierz wersję programu Microsoft Visual C++ Redistributable umożliwiająca DLL, która nie istnieje. Jeśli **zmiany** przycisk pojawia się na początku listy, wybierz go. Jeśli jest tylko opcja **Odinstaluj**, nie można naprawić tej wersji pakietu redystrybucyjnego.

3. Wybierz **naprawy** w oknie dialogowym Ustawienia pakietu redystrybucyjnego. Może być konieczne ponowne uruchomienie po zakończeniu naprawy.