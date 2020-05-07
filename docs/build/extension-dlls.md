---
title: Biblioteki DLL rozszerzeń
ms.date: 05/06/2019
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
ms.openlocfilehash: 55b1e55a9c7bdf6daaff98a7fe3f1a2a55f68334
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220762"
---
# <a name="mfc-extension-dlls"></a>Biblioteki DLL rozszerzeń MFC

Biblioteka DLL rozszerzenia MFC jest biblioteką DLL, która zwykle implementuje klasy wielokrotnego użytku, pochodzące z istniejących klas biblioteka MFC.

Biblioteka DLL rozszerzenia MFC ma następujące funkcje i wymagania:

- Plik wykonywalny klienta musi być aplikacją MFC skompilowaną `_AFXDLL` ze zdefiniowanym.

- Biblioteka DLL rozszerzenia MFC może być również używana przez zwykłą bibliotekę MFC DLL, która jest dynamicznie połączona z MFC.

- Biblioteki DLL rozszerzeń MFC powinny być kompilowane `_AFXEXT` ze zdefiniowanym. Te siły `_AFXDLL` są również zdefiniowane i gwarantują, że w plikach nagłówkowych MFC są pobierane odpowiednie deklaracje. Gwarantuje również, że `AFX_EXT_CLASS` jest on zdefiniowany `__declspec(dllexport)` jako podczas kompilowania biblioteki DLL, która jest niezbędna, jeśli to makro jest używane do DEKLAROWANIA klas w bibliotece DLL rozszerzenia MFC.

- Biblioteki DLL rozszerzenia MFC nie powinny tworzyć wystąpienia klasy pochodzącej od `CWinApp`, ale powinny polegać na aplikacji klienta (lub dll) w celu zapewnienia tego obiektu.

- Biblioteki DLL rozszerzenia MFC powinny jednak zapewnić `DllMain` funkcję i wykonać wszelkie niezbędne inicjalizacje.

Rozszerzenia bibliotek DLL są tworzone przy użyciu biblioteki dołączanej dynamicznie MFC (znanej również jako udostępniona wersja MFC). Tylko pliki wykonywalne MFC (aplikacje lub zwykłe biblioteki MFC DLL), które są tworzone przy użyciu udostępnionej wersji MFC, mogą korzystać z biblioteki DLL rozszerzenia MFC. Zarówno aplikacja kliencka, jak i Biblioteka DLL rozszerzenia MFC muszą używać tej samej wersji MFCx0. dll. Za pomocą biblioteki MFC DLL rozszerzenia można utworzyć nowe klasy niestandardowe z MFC, a następnie zaoferować tę rozszerzoną wersję MFC do aplikacji, które wywołują bibliotekę DLL.

Rozszerzenia bibliotek DLL mogą być również używane do przekazywania obiektów pochodnych MFC między aplikacją a biblioteką DLL. Funkcje składowe skojarzone z przekazanym obiektem istnieją w module, w którym został utworzony obiekt. Ponieważ te funkcje są prawidłowo eksportowane przy użyciu udostępnionej wersji biblioteki DLL MFC, można swobodne przekazywanie wskaźników obiektów pochodnych MFC lub MFC między aplikacjami i bibliotekami DLL rozszerzenia MFC, które ładuje.

Biblioteka DLL rozszerzenia MFC używa udostępnionej wersji MFC w taki sam sposób, w jaki aplikacja używa udostępnionej wersji biblioteki DLL MFC, z kilkoma dodatkowymi zagadnieniami:

- Nie ma `CWinApp`obiektu pochodnego. Musi ona współpracować z `CWinApp`obiektem pochodnym aplikacji klienckiej. Oznacza to, że aplikacja kliencka jest właścicielem głównej pompy komunikatów, pętli bezczynności i tak dalej.

- Wywołuje `AfxInitExtensionModule` `DllMain` funkcję. Wartość zwracana tej funkcji powinna być sprawdzona. Jeśli zwracana jest wartość zerowa z `AfxInitExtensionModule`, zwraca 0 z `DllMain` funkcji.

- Tworzy obiekt **CDynLinkLibrary** podczas inicjowania, jeśli biblioteka DLL rozszerzenia MFC chce eksportować `CRuntimeClass` obiekty lub zasoby do aplikacji.

Przed wersją 4,0 MFC, ten typ biblioteki DLL został wywołany jako AFXDLL. AFXDLL odwołuje się `_AFXDLL` do symbolu preprocesora, który jest definiowany podczas KOMPILOWANIA biblioteki DLL.

Biblioteki importu dla udostępnionej wersji MFC są nazwane zgodnie z Konwencją opisaną w [konwencjach nazewnictwa dla bibliotek DLL MFC](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions). Program Visual Studio dostarcza wstępnie skompilowane wersje bibliotek DLL MFC oraz szereg bibliotek DLL innych niż MFC, których można używać i rozpowszechniać z aplikacjami. Są one udokumentowane w Redist. txt, który jest instalowany w folderze Program Files\Microsoft Visual Studio.

Jeśli eksportujesz przy użyciu pliku. def, Umieść poniższy kod na początku i na końcu pliku nagłówkowego:

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Te cztery wiersze zapewniają poprawne skompilowanie kodu dla biblioteki DLL rozszerzenia MFC. Pozostawienie tych czterech wierszy może spowodować niewłaściwe skompilowanie biblioteki DLL lub łączenie się z nią.

Jeśli musisz przekazać wskaźnik obiektu MFC lub MFC-pochodnego do lub z biblioteki MFC DLL, biblioteka DLL powinna być biblioteką DLL rozszerzenia MFC. Funkcje składowe skojarzone z przekazanym obiektem istnieją w module, w którym został utworzony obiekt. Ponieważ te funkcje są prawidłowo eksportowane przy użyciu udostępnionej wersji biblioteki DLL MFC, można swobodne przekazywanie wskaźników obiektów pochodnych MFC lub MFC między aplikacjami i bibliotekami DLL rozszerzenia MFC, które ładuje.

Ze względu na problemy z dekorowanie i eksportowaniem nazw C++ lista eksportu z biblioteki DLL rozszerzenia MFC może różnić się między wersjami Debug i a DLL dla różnych platform. MFCx0. dll zawiera około 2 000 wyeksportowanych punktów wejścia; plik Debug MFCx0D. dll zawiera około 3 000 wyeksportowanych punktów wejścia.

## <a name="memory-management"></a>Zarządzanie pamięcią

MFCx0. dll i wszystkie biblioteki DLL rozszerzenia MFC załadowane do przestrzeni adresowej aplikacji klienckiej używają tego samego alokatora pamięci, ładowania zasobów i innych stanów globalnych MFC, tak jakby znajdowały się w tej samej aplikacji. Jest to istotne, ponieważ biblioteki DLL inne niż MFC i zwykłe biblioteki MFC są dokładnie takie same, jak w przypadku każdej biblioteki DLL, która alokuje z własnej puli pamięci.

Jeśli biblioteka DLL rozszerzenia MFC przydzieli pamięć, pamięć może swobodnie Intermix z dowolnym innym obiektem przydzielonym przez aplikację. Ponadto, jeśli aplikacja, która łączy się dynamicznie z MFC, nie powiedzie się, ochrona systemu operacyjnego zachowuje integralność każdej innej aplikacji MFC, która współużytkuje bibliotekę DLL.

Podobnie inne globalne Stany MFC, takie jak bieżący plik wykonywalny do ładowania zasobów z, są również udostępniane między aplikacją kliencką i wszystkimi bibliotekami DLL rozszerzenia MFC, a także MFCx0. dll.

## <a name="sharing-resources-and-classes"></a>Udostępnianie zasobów i klas

Eksportowanie zasobów odbywa się za pomocą listy zasobów. Każda aplikacja zawiera pojedynczo połączoną listę obiektów **CDynLinkLibrary** . Podczas wyszukiwania zasobu większość standardowych implementacji MFC, które ładują zasoby, wyszukuje najpierw w bieżącym module zasobów (`AfxGetResourceHandle`) i jeśli zasób nie zostanie znaleziony, przeprowadzi listę obiektów **CDynLinkLibrary** próbujących załadować żądany zasób.

Przechodzenie listy ma wady, które są nieco wolniejsze i wymaga zarządzania zakresami identyfikatorów zasobów. Ma ona zalety, aby aplikacja kliencka, która łączy się z kilkoma bibliotekami DLL rozszerzenia MFC, mogła używać dowolnego zasobu dostarczonego z biblioteką DLL bez konieczności określania dojścia do wystąpienia biblioteki DLL. `AfxFindResourceHandle`jest interfejsem API służącym do przechodzenia do listy zasobów w celu wyszukania danego dopasowania. Przyjmuje nazwę i typ zasobu i zwraca dojście do zasobu, w którym została najpierw znaleziona (lub ma wartość NULL).

Jeśli nie chcesz wyświetlać listy i ładować tylko zasoby z określonego miejsca, użyj funkcji `AfxGetResourceHandle` i `AfxSetResourceHandle` Zapisz stary uchwyt i Ustaw nowe dojście. Należy pamiętać o przywróceniu starego uchwytu zasobów przed zwróceniem do aplikacji klienckiej. Przykład użycia tego podejścia w celu jawnego załadowania menu można znaleźć w TESTDLL2. cpp w przykładowej MFC [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk).

Dynamiczne tworzenie obiektów MFC z daną nazwą MFC jest podobne. Mechanizm deserializacji obiektu MFC musi mieć wszystkie zarejestrowane `CRuntimeClass` obiekty, aby można je było odtworzyć przez dynamiczne tworzenie obiektów C++ dla wymaganego typu w oparciu o to, co zostało wcześniej zapisane.

W przypadku przykładowej [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk)MFC lista wygląda następująco:

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

gdzie *XX* jest numerem wersji; na przykład 42 reprezentuje wersję 4,2.

MFCxx. dll zwykle znajduje się na liście zasobów i klas. MFCxx. dll zawiera wszystkie standardowe zasoby MFC, w tym ciągi monitów dla wszystkich standardowych identyfikatorów poleceń. Umieszczenie go na końcu listy umożliwia Bibliotekom DLL i aplikacji klienckiej nie posiadanie własnej kopii standardowych zasobów MFC, ale w zamian polega na udostępnionych zasobach w MFCxx. dll.

Scalanie zasobów i nazw klas wszystkich bibliotek DLL w przestrzeni nazw aplikacji klienckiej ma wady związane z wymaganiem, aby należy zachować ostrożność z wybranymi identyfikatorami lub nazwami.

Przykład [DLLHUSK](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/dllhusk) służy do zarządzania współużytkowaną przestrzenią nazw zasobów przy użyciu wielu plików nagłówkowych.

Jeśli biblioteka DLL rozszerzenia biblioteki MFC musi obsługiwać dodatkowe dane dla każdej aplikacji, można utworzyć nową klasę z **CDynLinkLibrary** i tworzyć ją w `DllMain`. W trakcie działania Biblioteka DLL może sprawdzić listę obiektów **CDynLinkLibrary** bieżącej aplikacji, aby znaleźć tę dla danej biblioteki DLL rozszerzenia MFC.

### <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?

- [Inicjowanie biblioteki DLL rozszerzenia MFC](run-time-library-behavior.md#initializing-extension-dlls)

### <a name="what-do-you-want-to-know-more-about"></a>Jak chcesz dowiedzieć się więcej?

- [Porady dotyczące korzystania z udostępnionych plików zasobów](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)

- [Wersja biblioteki DLL MFC](../mfc/tn033-dll-version-of-mfc.md)

- [Zwykłe biblioteki DLL MFC połączone statycznie z MFC](regular-dlls-statically-linked-to-mfc.md)

- [Zwykłe biblioteki DLL MFC połączone dynamicznie z MFC](regular-dlls-dynamically-linked-to-mfc.md)

- [Korzystanie z bibliotek DLL rozszerzeń MFC w bazie danych, OLE i Sockets w zwykłych bibliotekach DLL MFC](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie bibliotek DLL C/C++ w programie Visual Studio](dlls-in-visual-cpp.md)
