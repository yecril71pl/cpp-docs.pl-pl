---
title: 'TN057: Lokalizacja składników MFC | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.mfc.components
dev_langs:
- C++
helpviewer_keywords:
- components [MFC], localizing
- TN057
- resources [MFC], localization
- localization [MFC], MFC resources
- localization [MFC], MFC components
- MFC DLLs [MFC], localizing
- DLLs [MFC], localizing MFC
- localization [MFC], resources
ms.assetid: 5376d329-bd45-41bd-97f5-3d895a9a0af5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8dcd3117d50d2d8905e5382cf226ba487c13a7c7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414215"
---
# <a name="tn057-localization-of-mfc-components"></a>TN057: lokalizacja składników MFC

> [!NOTE]
> Następująca uwaga techniczna nie został zaktualizowany od pierwszego uwzględnienia jej w dokumentacji online. W rezultacie niektóre procedury i tematy może być nieaktualne lub niepoprawne. Najnowsze informacje zaleca się wyszukać temat w indeksie dokumentacji online.

Ta uwaga opisuje niektóre projekty i procedury, których można użyć do zlokalizowania składnik, jeśli je kontrolować aplikację lub OLE lub biblioteki DLL, która używa biblioteki MFC.

## <a name="overview"></a>Omówienie

Istnieją dwa problemy można rozwiązać, gdy lokalizacja składnik, który korzysta z MFC. Najpierw musisz zlokalizować własne zasoby — ciągi, okna dialogowe i inne zasoby, które są specyficzne dla danego składnika. Większość składników utworzone przy użyciu biblioteki MFC, również zawierać i korzystają z szeregu zasobów, które są zdefiniowane przez MFC. Należy podać także zlokalizowane zasoby MFC. Na szczęście w niektórych językach są już udostępniane przez MFC sam.

Ponadto składnika powinna być przygotowana do uruchamiania w środowisku docelowym (środowisko Europejskiego lub włączone DBCS). W większości przypadków to zależy od aplikacji traktowanie znaki z zestawu wysokobitowych poprawnie i obsługa ciągów znaków dwubajtowych. MFC jest włączona, domyślnie dla obu tych środowiskach taki sposób, że można mieć jedną wartość binarną na całym świecie, jest używana na wszystkich platformach z zasobami po prostu inny podłączony w trakcie instalacji.

## <a name="localizing-your-components-resources"></a>Lokalizowanie zasobów danego składnika

Lokalizowanie aplikacji lub biblioteki DLL powinny obejmować zasoby, które jest zgodny z językiem docelowym po prostu zastępując zasobów. W przypadku własnych zasobów jest stosunkowo prosta: edytowanie zasobów w edytorze zasobów i skompilowaniu aplikacji usługi. Jeśli Twój kod jest zapisywane poprawnie nie będzie żadnych parametrów i tekst, który chcesz zlokalizować ustaloną do kodu źródłowego języka C++ — wszystkie lokalizacji może odbywać się po prostu modyfikując zasobów. W rzeczywistości można zaimplementować składnik, taki sposób, że wszystkie dostarczania zlokalizowanych wersji nawet pociąga za sobą kompilację oryginalny kod. Jest bardziej skomplikowana, ale jest warte i jest mechanizmem, który został wybrany dla MFC sam. Istnieje również możliwość lokalizowanie aplikacji ładowania pliku EXE lub DLL do edytora zasobów, a także bezpośrednio edytować zasoby. Ile jest to możliwe wymaga ponownego tych zmian za każdym razem, gdy tworzysz nową wersję aplikacji.

Jest jednym ze sposobów, aby uniknąć, aby zlokalizować wszystkie zasoby w oddzielnym pliku DLL czasami nazywane satelitarną bibliotekę DLL. Ta biblioteka DLL jest następnie ładowany dynamicznie w czasie wykonywania i zasoby są ładowane z tej biblioteki DLL zamiast z głównego modułu z całego kodu. Biblioteka MFC obsługuje bezpośrednio tego podejścia. Rozważmy aplikację o nazwie MYAPP. PLIK EXE; może mieć wszystkich jej zasobów znajdujących się w bibliotece DLL o nazwie MYRES. BIBLIOTEKI DLL. Przy stosowaniu `InitInstance` ją wykonać następujące polecenie, aby załadować tej biblioteki DLL i spowodować, że MFC, aby załadować zasoby z tej lokalizacji:

```cpp
CMyApp::InitInstance()
{
    // one of the first things in the init code
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)
        AfxSetResourceHandle(hInst);

    // other initialization code would follow
    // ...
}
```

Od tego momentu MFC załaduje zasoby z tej biblioteki DLL zamiast z myapp.exe. Wszystkie zasoby, jednak musi występować w tej bibliotece DLL; MFC nie wyszukiwanie wystąpienia aplikacji, w poszukiwaniu danego zasobu. Ta technika dotyczy równie dobrze do regularnego biblioteki MFC dll, a także formantów OLE. Program instalacyjny może spowodować skopiowanie odpowiednią wersję MYRES. Biblioteki DLL, w zależności od ustawień regionalnych zasobów, które użytkownik chce.

Stosunkowo łatwo utworzyć zasób tylko biblioteki DLL. Utwórz projekt biblioteki DLL, Dodawanie użytkownika. RC do niego i Dodaj wymagane zasoby. Jeśli masz istniejący projekt, który nie korzysta z tej techniki, możesz skopiować zasoby z tego projektu. Po dodaniu pliku zasobów do projektu, jesteś już prawie gotowe skompilować projekt. Jedyną czynnością, należy wykonać, jest, ustaw dla konsolidatora opcje dołączania **/noentry**. Informuje konsolidator, że biblioteka DLL nie ma punktu wejścia — ponieważ ma ona żadnego kodu, go nie ma punktu wejścia.

> [!NOTE]
> Edytor zasobów w Visual C++ 4.0 lub nowszym obsługuje wiele języków na. Plik RC. To może znacznie ułatwiają zarządzanie Twojej lokalizacji w jednym projekcie. Zasoby dla każdego języka są kontrolowane przez dyrektywy preprocesora, generowane przez Edytor zasobów.

## <a name="using-the-provided-mfc-localized-resources"></a>Przy użyciu podanego MFC zlokalizowane zasoby

Dowolnej aplikacji MFC, który kompilujesz ponownie używa dwie rzeczy z MFC: kod i zasoby. Oznacza to MFC posiada różne komunikaty o błędach, wbudowanych okien dialogowych i innych zasobów, które są używane przez klasy MFC. Aby całkowicie zlokalizować aplikację, musisz zlokalizować nie tylko zasobów aplikacji, ale również zasobów, które pochodzą bezpośrednio z MFC. Biblioteka MFC zawiera szereg różnych języka pliki zasobów automatycznie, tak, że jeśli język, którego obiektem docelowym jest jednym z języków, które już obsługuje MFC, wystarczy się upewnić, że używasz tych zlokalizowanych zasobów.

Na chwilę obecną, biblioteka MFC obsługuje chiński, niemiecki, hiszpański, francuski, włoski, japoński i koreańskim. Pliki, które zawierają te zlokalizowane wersje znajdują się w MFC\INCLUDE\L.* (oznaczonym literą "L" oznacza lokalizowanej) katalogów. Niemiecki pliki są MFC\INCLUDE\L.DEU, na przykład. Aby spowodować, że aplikacja korzysta z tych plików RC zamiast plików znajdujących się w MFC\INCLUDE, należy dodać `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` RC linii polecenia (jest to tylko przykładowe; należy zastąpić ustawienia regionalne, wybór, a także katalogu, w którym jest zainstalowany program Visual C ++).

Powyższe instrukcje będą działać, jeśli aplikacja łączy się statycznie z MFC. Większość aplikacji łączenie dynamiczne (ponieważ jest to domyślny przez kreatora AppWizard). W tym scenariuszu nie tylko kod jest dynamicznie połączone — dlatego są zasoby. W rezultacie można lokalizować zasoby w aplikacji, ale zasoby implementacji MFC będą nadal ładowane z MFC7x.DLL (lub nowszy) lub MFC7xLOC.DLL jeśli taki istnieje. Można to podejście, z dwoma różnymi kątami.

Bardziej skomplikowane podejście polega na statku, jeden zlokalizowane MFC7xLOC.DLLs (na przykład MFC7xDEU dla języka niemieckiego, MFC7xESP.DLL, hiszpański, itp.) lub nowszej wersji, a następnie zainstaluj odpowiednie MFC7xLOC.DLL w katalogu system, po użytkownik instaluje aplikację. To może być bardzo skomplikowane, dla deweloperów i użytkownika końcowego i jako takie nie jest zalecane. Zobacz [techniczne 56 Uwaga](../mfc/tn056-installation-of-localized-mfc-components.md) więcej informacji na temat tej techniki i jego ostrzeżenia.

Najprostszy i najbezpieczniejszy podejście ma zawierają zlokalizowane zasoby MFC w aplikacji lub biblioteki DLL samego (lub jego satelitarnej biblioteki DLL, korzystając z jednego). Umożliwia to uniknięcie problemów instalowania MFC7xLOC.DLL prawidłowo. Aby to zrobić, postępuj zgodnie z tych samych instrukcji, w przypadku statycznej podanej powyżej (ustawienie RC wiersza polecenia poprawnie, aby wskazać zlokalizowane zasoby), z wyjątkiem, musisz również usunąć `/D_AFXDLL` definiowanie, która została dodana przez kreatora AppWizard. Gdy `/D_AFXDLL` jest zdefiniowany, AFXRES. H (i inne pliki MFC RC) nie definiowania wszystkich zasobów (ponieważ one będzie pobierany z biblioteki MFC dll zamiast).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
