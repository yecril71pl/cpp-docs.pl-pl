---
title: "TN057: Lokalizacja składników MFC | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.components
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b8d8bcd21128b6d2d78d936e68f60040a75496c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tn057-localization-of-mfc-components"></a>TN057: lokalizacja składników MFC
> [!NOTE]
>  Poniższe uwagi techniczne nie został zaktualizowany, ponieważ została ona uwzględniona w dokumentacji online. W związku z tym niektóre procedury i tematy mogą być nieaktualne lub niepoprawne. Najnowsze informacje zalecane jest, możesz wyszukać temat odsetek w indeksie dokumentacji online.  
  
 Ta uwaga opisano niektóre z projektów i procedury, których można użyć do zlokalizowania składnika, jeśli ta aplikacja lub OLE kontroluje lub DLL, która używa MFC.  
  
## <a name="overview"></a>Omówienie  
 Istnieją dwa problemy można rozwiązać, gdy lokalizacja składnik, który używa MFC. Po pierwsze, musi zlokalizować własnych zasobów — ciągi, okna dialogowe i inne zasoby, które są specyficzne dla danego składnika. Większość składników utworzony za pomocą MFC również zawierać i używa wielu zasobów, które są zdefiniowane przez MFC. Należy podać także zlokalizowane zasoby MFC. Na szczęście kilku języków są już udostępniane przez MFC samej siebie.  
  
 Dodatkowo składnik powinna być przygotowana do działania w jego środowisku docelowym (środowisko Europejskiego lub funkcję). W większości przypadków zależy od aplikacji traktowanie znaki o wysokobitowe zestaw poprawnie i obsługi ciągi znaków dwubajtowych. MFC jest włączone, domyślnie dla obu tych środowisk, który będzie możliwe jedną wartość binarną na całym świecie używany na wszystkich platformach z właśnie różne zasoby podłączone w trakcie instalacji.  
  
## <a name="localizing-your-components-resources"></a>Twoje składnika zasoby lokalizacyjne  
 Lokalizowanie aplikacji lub biblioteki DLL powinny obejmować po prostu zastępowanie zasobów z zasobami, które odpowiada języka docelowego. Własnych zasobów jest stosunkowo proste: edytowanie zasobów w edytorze zasobów i skompilować aplikację. Jeśli kod jest zapisywane poprawnie nie będą istnieć nie ciągów lub tekst, który chcesz zlokalizować ustalony do kodu źródłowego języka C++ — lokalizacja wszystkie możliwe zmieniając po prostu zasobów. W rzeczywistości składnika można zaimplementować tak, aby wszystkie dostarczanie zlokalizowanej wersji nawet niepowodujący kompilacji oryginalnego kodu. Jest bardziej złożony, ale warto również go i jest wybrany dla MFC sam mechanizm. Istnieje również możliwość do zlokalizowania aplikacji podczas ładowania pliku EXE lub DLL do edytora zasobów i bezpośrednio edytując zasobów. Ile jest to możliwe wymaga ponownego tych zmian za każdym razem, gdy w przypadku tworzenia nowej wersji aplikacji.  
  
 Jednym ze sposobów uniknąć, który jest Znajdź wszystkie zasoby w oddzielnych bibliotekach DLL, nazywane również satelitarnej biblioteki DLL. Ta biblioteka DLL jest następnie ładowany dynamicznie w czasie wykonywania i zasoby są ładowane z tej biblioteki DLL zamiast z modułu głównego z całego kodu. MFC bezpośrednio obsługuje tej metody. Należy wziąć pod uwagę aplikacji o nazwie MOJAAPLIKACJA. EXE; może mieć wszystkich jej zasobów znajdujących się w bibliotece DLL o nazwie MYRES. BIBLIOTEKI DLL. W aplikacji `InitInstance` może wykonać następujące czynności, aby załadować tej biblioteki DLL i spowodować MFC załadować zasobów z tej lokalizacji:  
  
```  
CMyApp::InitInstance()  
{ *// one of the first things in the init code  
    HINSTANCE hInst = LoadLibrary("myres.dll");

    if (hInst != NULL)  
    AfxSetResourceHandle(hInst);

 *// other initialization code would follow  
 .  
 .  
 .  
}  
```  
  
 Następnie MFC z tej biblioteki DLL zamiast z myapp.exe załaduje zasobów. Wszystkie zasoby, jednak musi występować w tej bibliotece DLL; MFC nie umożliwia wyszukiwanie wystąpienia aplikacji w poszukiwaniu zasobu. Ta technika stosuje równie dobrze regularne biblioteki DLL MFC, jak również formantów OLE. Program Instalator będzie skopiować odpowiednią wersję MYRES. Biblioteki DLL w zależności od ustawień regionalnych zasobów, które ma zostać użytkownika.  
  
 Są one względnie łatwe utworzyć zasób tylko biblioteki DLL. Tworzenie projektu biblioteki DLL, Dodawanie użytkownika. RC plików do niego, a następnie dodaj wymagane zasoby. Jeśli masz istniejący projekt, który nie korzysta z tej metody można kopiować zasoby z tego projektu. Po dodaniu pliku zasobu do projektu, jesteś już prawie gotowe skompilować projekt. Jedyną operacją, należy wykonać jest opcji konsolidatora do uwzględnienia **/noentry**. Informuje konsolidator, że biblioteka DLL nie ma żadnego punktu wejścia — ponieważ go nie ma kodu, go nie ma wpisu punktu.  
  
> [!NOTE]
>  Edytor zasobów w programie Visual C++ 4.0 lub nowszym obsługuje wiele języków na. Plik RC. To może ułatwić bardzo łatwe w zarządzaniu Twojej lokalizacji w jednym projekcie. Zasoby dla każdego języka są kontrolowane przez dyrektywy preprocesora generowane przez Edytor zasobów.  
  
## <a name="using-the-provided-mfc-localized-resources"></a>Zasoby zlokalizowane przy użyciu podanego MFC  
 Dowolnej aplikacji MFC, której należy utworzyć ponownie używa dwóch elementów z MFC: kodu i zasobów. Oznacza to MFC ma różne komunikaty o błędach, wbudowanych okien dialogowych i innych zasobów, które są używane przez klas MFC. Aby całkowicie lokalizowanie aplikacji, należy do zlokalizowania nie tylko zasoby aplikacji, ale również zasobów, które są dostarczane bezpośrednio z MFC. MFC zapewnia szereg różnych językach pliki zasobów automatycznie, jeśli język, w którym ma być przeznaczona dla języków, które obsługuje już MFC, wystarczy upewnij się, że używasz tych zlokalizowanych zasobów.  
  
 Opracowywania tego tekstu MFC obsługuje chiński, niemiecki, hiszpański, francuski, włoski, japoński i koreański. Pliki, które zawierają te zlokalizowane wersje znajdują się w MFC\INCLUDE\L.* ("L" oznacza dla zlokalizowane) katalogów. Niemiecki pliki są MFC\INCLUDE\L.DEU, np. Aby spowodować, że aplikacja będzie korzystać z tych plików RC zamiast pliki znajdujące się w MFC\INCLUDE, Dodaj `/IC:\PROGRAM FILES\MICROSOFT VISUAL STUDIO .NET 2003\VC7\MFC\INCLUDE\L.DEU` RC linii polecenia (jest to tylko przykładowe; należy zastąpić ustawienia regionalne, wybór, a także katalogu, w którym jest zainstalowany program Visual C ++).  
  
 Powyższe instrukcje będzie działać, jeśli aplikacja łączy statycznie z MFC. Większość aplikacji łącze dynamicznie (ponieważ jest to wartość domyślna kreatorami AppWizard). W tym scenariuszu nie tylko kod jest dynamicznie połączony - są zasoby. W związku z tym można lokalizować zasobami w aplikacji, ale zasoby MFC wdrożenia będą nadal ładowane z MFC7x.DLL (lub nowszy) lub MFC7xLOC.DLL Jeśli istnieje. Można to podejścia z dwoma różnymi kątami.  
  
 Bardziej złożone podejście jest dostarczać jedną zlokalizowanych MFC7xLOC.DLLs (na przykład MFC7xDEU na język niemiecki, MFC7xESP.DLL, hiszpański, itp.) lub nowszy i zainstalować odpowiednią MFC7xLOC.DLL w katalogu systemu, kiedy użytkownik instaluje aplikację. To może być bardzo skomplikowane dla deweloperów i użytkownika końcowego i jako taki nie jest zalecane. Zobacz [56 Uwaga techniczna](../mfc/tn056-installation-of-localized-mfc-components.md) uzyskać więcej informacji na temat tej techniki i jego ostrzeżenia.  
  
 Najprostsza i najbezpieczniejszy podejście jest uwzględnienie zlokalizowane zasoby MFC w aplikacji lub biblioteki DLL samego (lub jej satelitarnej biblioteki DLL, jeśli używasz). Dzięki temu można uniknąć problemów poprawnie zainstalować MFC7xLOC.DLL. Aby to zrobić, należy wykonać instrukcje w przypadku statycznej powyższych (ustawienie RC wiersza polecenia poprawnie, aby wskazywały zlokalizowanych zasobów), z wyjątkiem czy należy również usunąć `/D_AFXDLL` zdefiniować, która została dodana przez kreatorami AppWizard. Gdy `/D_AFXDLL` jest zdefiniowany AFXRES. H (i innych plików MFC RC) nie faktycznie definiują żadnych zasobów (ponieważ są one będą pobrania z biblioteki DLL MFC zamiast niego).  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

