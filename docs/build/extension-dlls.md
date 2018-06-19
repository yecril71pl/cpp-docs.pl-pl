---
title: Biblioteki DLL rozszerzeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- afxdll
dev_langs:
- C++
helpviewer_keywords:
- memory [C++], DLLs
- MFC extension DLLs [C++]
- AFXDLL library
- shared resources [C++]
- MFC DLLs [C++], MFC extension DLLs
- DLLs [C++], extension
- shared DLL versions [C++]
- resource sharing [C++]
- extension DLLs [C++]
- extension DLLs [C++], about MFC extension DLLs
ms.assetid: f69ac3d4-e474-4b1c-87a1-6738843a135c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f60540735be44adf4305dcda77373faf8a83514
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377134"
---
# <a name="mfc-extension-dlls"></a>Biblioteki DLL rozszerzeń MFC
Rozszerzenia MFC DLL jest bibliotekę DLL, która zwykle implementuje klasy wielokrotnego użytku, pochodnych istniejące klasy Microsoft Foundation Class Library.  
  
 Biblioteka DLL rozszerzenia MFC ma następujące funkcje i wymagania:  
  
-   Plik wykonywalny klienta musi być skompilowana przy użyciu aplikacji MFC `_AFXDLL` zdefiniowane.  
  
-   Biblioteki DLL rozszerzenia MFC mogą również posłużyć regularne biblioteki DLL MFC, która jest połączona dynamicznie z MFC.  
  
-   Biblioteki DLL rozszerzeń MFC ma być kompilowana przy użyciu `_AFXEXT` zdefiniowane. Dzięki temu `_AFXDLL` należy również określić i upewnia się, że odpowiednie deklaracje są pobierane z plików nagłówek MFC. Gwarantuje również, że `AFX_EXT_CLASS` jest zdefiniowany jako `__declspec(dllexport)` podczas tworzenia biblioteki DLL, która jest wymagana, jeśli używasz tego makra, aby zadeklarować klasy w bibliotekę DLL rozszerzenia MFC.  
  
-   Biblioteki DLL rozszerzeń MFC nie utworzyć wystąpienia klasy pochodzącej od `CWinApp`, ale polegać na aplikacji klienckiej (lub DLL) zapewnienie tego obiektu.  
  
-   Biblioteki DLL rozszerzeń MFC, należy podać `DllMain` funkcji i wykonaj wszystkie niezbędne inicjowania.  
  
 Biblioteki DLL rozszerzeń są tworzone przy użyciu wersji biblioteki DLL MFC (znanej także jako udostępniony wersja MFC). Tylko MFC pliki wykonywalne (aplikacji lub MFC dll), które są tworzone przy użyciu udostępnionych wersji biblioteki MFC, można użyć rozszerzenia MFC DLL. Zarówno aplikacja klienta, jak i bibliotekę DLL rozszerzenia MFC musi używać tej samej wersji MFCx0.dll. Z rozszerzeniem MFC DLL może wyprowadzać nowe klasy w niestandardowych z MFC i następnie oferowanie ta rozszerzona wersja MFC, aby aplikacje, które wywołują biblioteki DLL.  
  
 Biblioteki DLL rozszerzeń można również może być przekazywany pochodnych MFC obiektów między aplikacją a biblioteki DLL. Funkcje Członkowskie skojarzony z obiektem przekazany istnieje w module, w której został utworzony obiekt. Ponieważ te funkcje są poprawnie eksportowane, używając udostępnionych wersja biblioteki DLL MFC, za darmo można przekazać MFC lub wskaźniki obiektu pochodnego MFC pomiędzy aplikacją i ładuje biblioteki DLL rozszerzenia MFC.  
  
 Rozszerzenia MFC DLL używa wersji udostępnionego MFC tak samo jak aplikacja używa udostępnionego wersja biblioteki DLL MFC, z kilku uwagi dodatkowe:  
  
-   Nie ma `CWinApp`-pochodzi z obiektu. Należy skontaktować się z `CWinApp`-pochodnych obiektu aplikacji klienta. Oznacza to, że aplikacja kliencka jest właścicielem pompa głównej wiadomości, pętli bezczynności i tak dalej.  
  
-   Wywołuje `AfxInitExtensionModule` w jego `DllMain` funkcji. Wartość zwracana tej funkcji powinna być sprawdzana. Jeśli wartość zero, jest zwracana z `AfxInitExtensionModule`, zwraca 0 z Twojej `DllMain` funkcji.  
  
-   Tworzy **CDynLinkLibrary** obiektu podczas inicjowania, jeśli rozszerzenia MFC DLL chce wyeksportować `CRuntimeClass` obiektów lub zasobów do aplikacji.  
  
 Przed wersja 4.0 MFC DLL tego typu została wywołana AFXDLL. AFXDLL odwołuje się do `_AFXDLL` symbol preprocesora, który jest definiowany podczas tworzenia biblioteki DLL.  
  
 Biblioteki importu dla udostępnionych wersja MFC są nazywane zgodnie z Konwencją opisanego w [konwencje nazewnictwa bibliotek MFC dll](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual C++ udostępnia wbudowane wersje biblioteki MFC dll, a także numer z innych niż biblioteki DLL MFC, który można użyć i rozpowszechniać w aplikacjach. Te są udokumentowane w artykule Redist.txt, który jest instalowany w folderze Program Files\Microsoft Visual Studio.  
  
 Jeśli eksportujesz przy użyciu pliku .def następujący kod należy umieścić na początku i na końcu pliku nagłówka:  
  
```cpp  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 Te wiersze cztery upewnij się poprawnie kompilowania kodu dla biblioteki DLL rozszerzenia MFC. Pozostawienie tych czterech wierszy może spowodować biblioteki DLL do kompilacji lub połączyć niepoprawnie.  
  
 Jeśli musisz przekazać MFC lub wskaźnik do obiektu pochodnego MFC z biblioteki DLL MFC DLL lub powinny być bibliotekę DLL rozszerzenia MFC. Funkcje Członkowskie skojarzony z obiektem przekazany istnieje w module, w której został utworzony obiekt. Ponieważ te funkcje są poprawnie eksportowane, używając udostępnionych wersja biblioteki DLL MFC, za darmo można przekazać MFC lub wskaźniki obiektu pochodnego MFC pomiędzy aplikacją i ładuje biblioteki DLL rozszerzenia MFC.  
  
 Z powodu problemów przekręcona i eksportowanie C++ nazwę na liście eksportu z rozszerzenia MFC DLL mogą się różnić między debugowania i detalicznej wersji tego samego pliku dll i biblioteki DLL dla różnych platform. Detaliczne MFCx0.dll ma około 2000 wyeksportowane punktów wejścia. Debuguj MFCx0D.dll ma około 3000 punkty wejścia wyeksportowanej.  
  
## <a name="memory-management"></a>Zarządzanie pamięcią  
 MFCx0.dll i wszystkie rozszerzenia MFC, które biblioteki DLL ładowane do przestrzeni adresowej aplikacji klienta należy użyć tego samego alokatora, ładowania zasobów i innych stanów globalne MFC, jak gdyby znajdowały się w tej samej aplikacji. Jest to istotne, ponieważ biblioteki z systemem innym niż MFC DLL i regularne biblioteki DLL MFC nie dokładnym przeciwieństwem i mieć każdej biblioteki DLL przydziału poza własną pulę pamięci.  
  
 Jeśli bibliotekę DLL rozszerzenia MFC przydziela pamięć, pamięci, można swobodnie intermix z innym obiektem przydzielone aplikacji. Jeśli aplikacja łączy dynamicznie z MFC nie powiedzie się, ochronę systemu operacyjnego zachowuje również integralność innych aplikacji MFC, udostępnianie biblioteki DLL.  
  
 Podobnie innych stanów globalne MFC, jak bieżący plik wykonywalny do ładowania zasobów, są również współużytkowane aplikacji klienckiej i wszystkie biblioteki DLL rozszerzenia MFC także MFCx0.dll się.  
  
## <a name="sharing-resources-and-classes"></a>Udostępnianie zasobów i klasy  
 Eksportowanie zasobów odbywa się za pośrednictwem listy zasobów. Każda aplikacja zawiera listę pojedynczo połączonego **CDynLinkLibrary** obiektów. Podczas wyszukiwania dla zasobu, większość standardowych implementacji MFC, które ładują zasobów przyjrzeć bieżącego modułu zasobów (`AfxGetResourceHandle`), a jeśli nie znaleziono zasobu zawiera listę **CDynLinkLibrary** obiektów Próba załadowania żądanego zasobu.  
  
 Przejście na liście ma wady jest wolniejsze i wymaga zarządzania zakresami identyfikator zasobu. Ma ona zaletą aplikacji klienta, który stanowi łącze do kilku bibliotek DLL rozszerzeń MFC można użyć dowolnego dostarczane do biblioteki DLL zasobu bez konieczności określania dojście wystąpienia biblioteki DLL. `AfxFindResourceHandle` Interfejs API służy do przejście listę zasobów do wyszukiwania dla danego dopasowania. Pobiera nazwę i typ zasobu, a zwraca dojście do zasobu którym najpierw zostało znalezione (lub wartość NULL).  
  
 Jeśli nie chcesz przeprowadzić liście i ładować tylko zasoby z określonym miejscu, należy użyć funkcji `AfxGetResourceHandle` i `AfxSetResourceHandle` zapisać dojście stary i ustawić nowy uchwyt. Pamiętaj przywrócić stary dojście do zasobu przed zwróceniem do aplikacji klienckiej. Na przykład w sposób jawny załadować menu przy użyciu tej metody, zobacz .cpp Testdll2 w przykładowym MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).  
  
 Przypomina dynamiczne tworzenie obiektów MFC otrzymuje nazwę MFC. Mechanizm deserializacji obiektu MFC musi mieć wszystkie `CRuntimeClass` obiektów zarejestrowana, dzięki czemu można go odtworzyć za dynamiczne tworzenie obiektów C++ wymaganego typu co wcześniej była przechowywana w oparciu.  
  
 W przypadku przykładowej MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk), listy wygląda mniej więcej tak:  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
               |                      |  
          TESTDLL2.DLL           TESTDLL2.DLL  
               |                      |  
          TESTDLL1.DLL           TESTDLL1.DLL  
               |                      |  
           MFCOxxD.DLL                |  
               |                      |  
           MFCDxxD.DLL                |  
               |                      |  
            MFCxxD.DLL            MFCxx.DLL  
```  
  
 gdzie *xx* jest numer wersji; na przykład 42 reprezentuje wersji 4.2.  
  
 MFCxx.dll jest zazwyczaj ostatnie na liście klas i zasobów. MFCxx.dll zawiera wszystkie standardowe zasoby MFC, w tym ciągów monitu wszystkie identyfikatory poleceń standardowych. Umieszczenia go na końcu listy umożliwia biblioteki dll i samej aplikacji klienta nie ma swoje własne kopie standardowe zasoby MFC, ale zależne od zasobów udostępnionych w MFCxx.dll zamiast tego.  
  
 Scalanie zasobów i nazwy klas wszystkich bibliotek DLL w przestrzeni nazw aplikacja kliencka ma wadą konieczności należy zachować ostrożność, z jakiego wyborze nazwy lub identyfikatory.  
  
 [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) próbki zarządza przestrzeń nazw udostępnionych zasobów przy użyciu wielu plików nagłówka.  
  
 Jeśli bibliotekę DLL rozszerzenia MFC musi obsługiwać dodatkowe dane dla każdej aplikacji, może pochodzić z nową klasę **CDynLinkLibrary** i utwórz go w `DllMain`. Podczas uruchamiania, plik DLL, który można sprawdzić listę bieżącej aplikacji **CDynLinkLibrary** obiektów do znalezienia dla konkretnego rozszerzenia MFC DLL.  
  
### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Inicjowanie biblioteki DLL rozszerzenia MFC](../build/run-time-library-behavior.md#initializing-extension-dlls)  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Wskazówki dotyczące korzystania z zasobów udostępnionych plików](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)  
  
-   [Wersja biblioteki DLL MFC](../mfc/tn033-dll-version-of-mfc.md)  
  
-   [Regularne biblioteki DLL MFC połączone statycznie z MFC](../build/regular-dlls-statically-linked-to-mfc.md)  
  
-   [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](../build/regular-dlls-dynamically-linked-to-mfc.md)  
  
-   [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](../build/using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)