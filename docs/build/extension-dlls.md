---
title: Biblioteki DLL rozszerzeń
ms.date: 11/04/2016
f1_keywords:
- afxdll
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
ms.openlocfilehash: eca33b60b8fa6ba812bf5fa68520f51ceb1d164b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195663"
---
# <a name="mfc-extension-dlls"></a>Biblioteki DLL rozszerzeń MFC

Rozszerzenia MFC biblioteki DLL jest biblioteki DLL, które zazwyczaj implementują klasy wielokrotnego użytku pochodzące z istniejących klas biblioteki klas Microsoft Foundation.

Rozszerzenia MFC biblioteki DLL ma następujące cechy i wymagania:

- Klient wykonywalny musi być skompilowany przy użyciu aplikacji MFC `_AFXDLL` zdefiniowane.

- Można także rozszerzenia MFC biblioteki DLL według zwykłej biblioteki MFC DLL, która jest połączona dynamicznie z MFC.

- Biblioteki DLL rozszerzeń MFC powinna być skompilowana przy użyciu `_AFXEXT` zdefiniowane. Zmusza to `_AFXDLL` należy także zdefiniować i zapewnia, że odpowiednie deklaracji jest pobierane z plikach nagłówkowych MFC. Gwarantuje również, że `AFX_EXT_CLASS` jest zdefiniowany jako `__declspec(dllexport)` podczas kompilowania biblioteki DLL, który jest niezbędny, jeśli używasz tego makra do deklarowania klas w rozszerzeniu MFC DLL.

- Biblioteki DLL rozszerzeń MFC nie utworzyć wystąpienia klasy pochodzącej od `CWinApp`, ale powinny korzystać z aplikacji klienta (lub DLL) do zapewnienia tego obiektu.

- Biblioteki DLL rozszerzeń MFC jednak dostarczają `DllMain` działać, a następnie wykonaj wszelkie niezbędne inicjowania.

Biblioteki DLL rozszerzeń są kompilowane przy użyciu wersji biblioteki DLL MFC (znany także jako udostępnionej wersja MFC). Tylko pliki wykonywalne MFC (aplikacji lub zwykłych bibliotekach MFC dll), które są tworzone za pomocą udostępnionej wersja MFC można użyć rozszerzenia MFC biblioteki DLL. Zarówno aplikacja klienta, jak i rozszerzenia MFC biblioteki DLL, należy użyć tej samej wersji MFCx0.dll. Za pomocą rozszerzenia MFC biblioteki DLL może wyprowadzać nowe klasy niestandardowej z MFC i następnie oferują tej rozszerzonej wersji biblioteki MFC do aplikacji, które wywołują bibliotekę DLL.

Biblioteki DLL rozszerzeń również może służyć do przekazywania obiekty pochodzące z MFC między aplikacją a biblioteki DLL. Funkcje elementów członkowskich skojarzonych z przekazany obiekt istnieje w module, w której został utworzony obiekt. Ponieważ te funkcje są prawidłowo wyeksportowana, korzystając z udostępnionej wersja dll biblioteki MFC, można przekazać za darmo MFC lub wskaźniki obiektów klasy pochodnej MFC między aplikacją a rozszerzenia MFC biblioteki dll, ładuje.

Biblioteka DLL rozszerzenia MFC używa udostępnionej wersja MFC w taki sam sposób, w aplikacji za pomocą udostępnionych wersji biblioteki DLL MFC, kilka dodatkowych kwestii dotyczących:

- Nie ma `CWinApp`-pochodnych obiektu. Należy skontaktować się z `CWinApp`-pochodzi obiekt aplikacji klienckiej. Oznacza to, czy aplikacja kliencka jest właścicielem pompy komunikatów głównym, wykonywania pętli bezczynności i tak dalej.

- Wywołuje `AfxInitExtensionModule` w jego `DllMain` funkcji. Wartość zwracana przez tę funkcję, powinno być zaznaczone. Jeśli zwracana jest wartość zero z `AfxInitExtensionModule`, zwracają 0 z Twojej `DllMain` funkcji.

- Tworzy **CDynLinkLibrary** obiektu podczas inicjowania, jeśli chce biblioteki DLL rozszerzeń MFC, aby wyeksportować `CRuntimeClass` obiektów lub zasobów do aplikacji.

Przed wersją 4.0, MFC tego rodzaju DLL została wywołana AFXDLL. AFXDLL odwołuje się do `_AFXDLL` symbol preprocesora, który jest definiowany podczas tworzenia biblioteki DLL.

Bibliotek importu dla udostępnionej wersja MFC są określane według Konwencji opisanego w [konwencje nazewnictwa bibliotek MFC dll](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Visual C++ dostarcza wbudowanych wersje biblioteki MFC dll, a także numer z innych niż - biblioteki MFC dll, którą można użyć i rozpowszechniać za pomocą aplikacji. Te są udokumentowane w Redist.txt, który jest zainstalowany w folderze Program Files\Microsoft Visual Studio.

Jeśli eksportujesz używając pliku .def, umieść następujący kod na początku i na końcu pliku nagłówka:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Te cztery wiersze upewnij się, że kod jest kompilowany poprawnie dla rozszerzenia MFC biblioteki DLL. Pomijając tych czterech linii może spowodować bibliotekę DLL do kompilacji lub niepoprawne łączenie.

Jeśli musisz przekazać MFC lub wskaźnik do obiektu klasy pochodnej MFC z biblioteki MFC DLL, biblioteka DLL lub powinny być rozszerzenia MFC biblioteki DLL. Funkcje elementów członkowskich skojarzonych z przekazany obiekt istnieje w module, w której został utworzony obiekt. Ponieważ te funkcje są prawidłowo wyeksportowana, korzystając z udostępnionej wersja dll biblioteki MFC, można przekazać za darmo MFC lub wskaźniki obiektów klasy pochodnej MFC między aplikacją a rozszerzenia MFC biblioteki dll, ładuje.

Ze względu na problemy przekręcaniu i eksportowanie C++ nazwy Eksportuj listę z rozszerzenia MFC biblioteki DLL mogą się różnić między debugowania, jak i sprzedaży detalicznej wersji tej samej biblioteki DLL i bibliotek DLL dla różnych platform. Handlu detalicznego MFCx0.dll ma około 2000 wyeksportowane punkty wejścia; debugowanie MFCx0D.dll ma około 3000 punkty wejścia wyeksportowanej.

## <a name="memory-management"></a>Zarządzanie pamięcią

MFCx0.dll i wszystkich rozszerzeń MFC, które biblioteki DLL ładowane do aplikacji klienckiej przestrzeń adresową należy używać tego samego alokatora pamięci, ładowanie zasobów i inne stany globalne MFC tak, jakby znajdowały się w tej samej aplikacji. Jest to znaczące, ponieważ biblioteki DLL bez MFC i zwykłych bibliotekach MFC dll czy dokładnym przeciwieństwem ale przydzielanie każdej biblioteki DLL z puli pamięci.

Jeśli biblioteka DLL rozszerzenia MFC przydziela pamięci, pamięci można swobodnie intermix z innym obiektem przydzielone aplikacji. Ponadto w przypadku awarii aplikacji, która łączy dynamicznie MFC ochronę systemu operacyjnego zachowywana jest integralność innych aplikacji MFC, udostępnianie biblioteki DLL.

Podobnie innych Państw globalne MFC, takich jak bieżący plik wykonywalny można załadować zasobów, są również współużytkowane aplikacji klienckiej i wszystkie biblioteki DLL rozszerzeń MFC także MFCx0.dll sam.

## <a name="sharing-resources-and-classes"></a>Udostępnianie zasobów i klas

Eksportowanie zasobów odbywa się za pośrednictwem listy zasobów. Każda aplikacja zawiera pojedynczo połączoną listę **CDynLinkLibrary** obiektów. Podczas wyszukiwania zasobu, większość standardowych implementacji MFC, które ładowanie zasobów przyjrzeć bieżącego modułu zasobów (`AfxGetResourceHandle`) i jeśli nie można odnaleźć zasobu zapoznaj się z listy **CDynLinkLibrary** obiektów Podjęto próbę załadowania żądanego zasobu.

Zalet listy ma wad jest wolniejsze i wymaga zarządzania zakresami identyfikator zasobu. Ma tę zaletę, że aplikacja kliencka, który stanowi łącze do kilku bibliotek DLL rozszerzeń MFC można użyć dowolnego zasobu dostarczone przez bibliotekę DLL bez konieczności określania dojście wystąpienia biblioteki DLL. `AfxFindResourceHandle` Interfejs API służy do zalet listy zasobów do wyszukania danego dopasowania. Ona przyjmuje nazwę i typ zasobu i zwraca wartość, gdzie najpierw został znaleziony dojście do zasobu (lub wartość NULL).

Jeśli nie chcesz, zapoznaj się z listy i ładować tylko zasoby w określonym miejscu, użyj funkcji `AfxGetResourceHandle` i `AfxSetResourceHandle` zapisać stary dojścia i ustaw nowy uchwyt. Pamiętaj przywrócić stare dojście do zasobu, aby powrócić do aplikacji klienckiej. Na przykład użycia tej metody, aby jawnie załadować menu zobacz .cpp Testdll2 próbki MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

Dynamiczne tworzenie obiektów MFC otrzymuje nazwę MFC jest podobny. Mechanizm deserializacji obiektu MFC musi mieć wszystkie `CRuntimeClass` obiekty zarejestrowane tak, aby go odtworzyć za dynamiczne tworzenie obiektów C++ wymagany typ oparte na co wcześniej została zapisana.

W tym przykładzie MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk), listy wygląda mniej więcej tak:

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

gdzie *xx* jest numerem wersji; na przykład 42 reprezentuje wersję 4.2.

MFCxx.dll jest zwykle ostatni zasób i lista klas. MFCxx.dll obejmuje wszystkie standardowe zasoby MFC, w tym ciągi monitu wszystkie identyfikatory poleceń standardowych. Umieszczając go na końcu listy umożliwia bibliotek DLL i samej aplikacji klienckiej nie mają własnej kopii standardowe zasoby MFC, ale polegają na zasoby udostępnione w MFCxx.dll zamiast tego.

Scalanie zasobów i nazwy klasy wszystkie biblioteki dll w przestrzeni nazw aplikacji klienta ma wadą konieczności Uważaj, jakie identyfikatory lub wybrania nazwy.

[DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) przykładowe zarządza przestrzeń nazw udostępnionych zasobów przy użyciu wiele plików nagłówkowych.

Jeśli biblioteka DLL rozszerzenia MFC musi obsługiwać dodatkowe dane dla każdej aplikacji, można uzyskać nowe klasy z **CDynLinkLibrary** i utworzyć ją w `DllMain`. Podczas uruchamiania, biblioteki DLL, można sprawdzić listę bieżącej aplikacji **CDynLinkLibrary** obiektu do znalezienia dla tego określonego rozszerzenia MFC biblioteki DLL.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Inicjowanie biblioteki DLL rozszerzenia MFC](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

- [Porady dotyczące korzystania z zasobów udostępnionych plików](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [Wersja dll biblioteki MFC](../mfc/tn033-dll-version-of-mfc.md)

- [Regularne biblioteki DLL MFC połączone statycznie z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Regularne biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Używanie bibliotek DLL baz danych, OLE i rozszerzeń MFC gniazd w zwykłych bibliotekach MFC DLL](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Zobacz także

[Biblioteki DLL w programie Visual C++](dlls-in-visual-cpp.md)
