---
title: 'TN033: wersja DLL biblioteki MFC'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.dll
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: 89a9fddd6f12f92d18bcd6fc75f117beb14746f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571824"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: wersja DLL biblioteki MFC

Ta uwaga opisuje, jak można użyć MFCxx.DLL i MFCxxD.DLL (gdzie x jest numerem wersji MFC) udostępniane biblioteki łączone dynamicznie z aplikacjami MFC oraz biblioteki DLL rozszerzeń MFC. Aby uzyskać więcej informacji na temat regularnych bibliotek DLL MFC, zobacz [przy użyciu biblioteki MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Ta uwaga techniczna obejmuje trzy aspekty biblioteki dll. Ostatnie dwa są dla bardziej zaawansowanych użytkowników:

- [Tworzenie biblioteki DLL rozszerzenia MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Tworzenie aplikacji MFC, która korzysta z wersji biblioteki DLL MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Jak MFC udostępnionych bibliotek DLL są implementowane](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Jeśli interesuje Cię Tworzenie biblioteki DLL przy użyciu biblioteki MFC, które mogą być używane z innego typu niż MFC aplikacji (jest to nazywane zwykłej biblioteki MFC DLL), zapoznaj się [techniczne Uwaga 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Omówienie obsługi MFCxx.DLL: terminologii i pliki

**Regularne biblioteki DLL MFC**: używasz regularnej biblioteki DLL MFC do tworzenia autonomicznych biblioteki DLL, przy użyciu niektórych klas MFC. Interfejsy granicę aplikacji/DLL są interfejsy "C", a aplikacja kliencka nie musi być aplikacji MFC.

To jest wersja Obsługa DLL obsługiwane w wersji 1.0 z MFC. Jest on opisany w [techniczne Uwaga 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) i próbce zaawansowanych koncepcji MFC [DLLScreenCap](../visual-cpp-samples.md).

> [!NOTE]
> Począwszy od Visual C++ w wersji 4.0 termin **USRDLL** jest przestarzały i został zastąpiony przez zwykłej biblioteki MFC DLL, która statycznie łączy się MFC. Mogą także tworzyć zwykłej biblioteki MFC DLL, która łączy dynamicznie z MFC.

MFC 3.0 (i nowsze wersje) obsługuje zwykłych bibliotekach MFC dll z nowych funkcji, łącznie z klasy OLE i bazy danych.

**AFXDLL**: to jest również nazywany udostępnionych wersji biblioteki MFC. Jest to nowe biblioteki DLL dodano obsługę MFC w wersji 2.0. Sama biblioteka MFC jest w szeregu bibliotek DLL (opisanych poniżej), a aplikacja kliencka lub biblioteki DLL dynamicznie łączy biblioteki dll, które są wymagane. Interfejsy granicę aplikacji/DLL są w języku C + +/ interfejsu klasy MFC. Aplikacja kliencka musi być aplikacji MFC. To obsługuje wszystkie funkcje MFC 3.0 (wyjątek: UNICODE nie jest obsługiwane dla klas baz danych).

> [!NOTE]
> Począwszy od Visual C++ w wersji 4.0 tego rodzaju DLL nazywa się "Rozszerzeniem DLL."

Ta uwaga użyje MFCxx.DLL do odwoływania się do całego ustawionych biblioteki MFC DLL, która obejmuje:

- Debugowanie: MFCxxD.DLL (połączona) i MFCSxxD.LIB (statyczny).

- Wydanie: MFCxx.DLL (połączona) i MFCSxx.LIB (statyczny).

- Debugowanie kodu Unicode: MFCxxUD.DLL (połączona) i MFCSxxD.LIB (statyczny).

- Wersja Unicode: MFCxxU.DLL (połączona) i MFCSxxU.LIB (statyczny).

> [!NOTE]
> MFCSxx [U] [D]. Biblioteki LIB są używane w połączeniu z MFC współdzielonych bibliotek DLL. Biblioteki te zawierają kod, który musi być połączone statycznie z aplikacji lub biblioteki DLL.

Linki z aplikacji do odpowiednich Importuj biblioteki:

- Debugowanie: MFCxxD.LIB

- Wydanie: MFCxx.LIB

- Debugowanie kodu Unicode: MFCxxUD.LIB

- Wersja Unicode: MFCxxU.LIB

"MFC biblioteki DLL rozszerzenia" jest plikiem utworzonych na podstawie MFCxx.DLL (i/lub inne MFC współdzielonych bibliotek DLL). W tym miejscu architektury składników MFC aktywowany. Jeśli wyprowadzenia klasy przydatne z klasy MFC lub innego MFC podobny zestaw narzędzi do kompilacji, należy go umieścić w bibliotece DLL. Czy biblioteka DLL używa MFCxx.DLL, podobnie jak aplikacja kliencka ultimate. Pozwala to na klasy wielokrotnego użytku widok/dokumentu, klasy bazowe wielokrotnego użytku i klasy wielokrotnego użytku typu liść.

## <a name="pros-and-cons"></a>Zalety i wady

Dlaczego należy używać udostępnionej wersja MFC

- Przy użyciu biblioteki udostępnionej może spowodować mniejszych aplikacji (minimalną aplikację, która wykorzystuje większość biblioteki MFC jest mniejsza niż 10 tys.).

- Udostępnionej wersja MFC obsługuje bibliotek DLL rozszerzeń MFC i zwykłych bibliotekach MFC DLL.

- Kompilowania aplikacji korzystającej z udostępnionej biblioteki MFC jest szybsza niż kompilowanie statycznie łączonych aplikacji MFC, ponieważ nie jest konieczne samo łąćzneie z MFC. Jest to szczególnie istotne w **debugowania** kompilacji, gdzie konsolidator musi zmniejszyć informację debugowania — poprzez łączenie się z biblioteki DLL, która już zawiera informacje o debugowaniu, jest mniej informacji debugowania do kompaktowania w aplikacji.

Dlaczego użytkownik nie należy używać udostępnionej wersja MFC:

- Wysyłanie aplikacji korzystającej z biblioteki udostępnionej wymaga dostarczasz MFCxx.DLL (i inne) biblioteki w programie. MFCxx.DLL jest swobodnie do dystrybucji, takich jak liczby bibliotek DLL, ale trzeba mimo to zainstalować biblioteki DLL w programie Instalatora. Ponadto należy dostarczyć MSVCRTxx.DLL, który zawiera biblioteki środowiska uruchomieniowego C, który jest używany zarówno przez program i same biblioteki MFC DLL.

##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a> Jak napisać biblioteki DLL rozszerzenia MFC

Biblioteka DLL rozszerzenia MFC jest biblioteki DLL zawierającej klasy i funkcje zapisywane ozdobić funkcje klas MFC. Biblioteka DLL rozszerzenia MFC używa udostępnionej biblioteki MFC DLL tak samo jak aplikacja używa, kilka dodatkowych kwestii dotyczących:

- Proces kompilacji jest podobny do kompilowania aplikacji korzystającej z biblioteki MFC udostępnione pewne dodatkowe kompilatora i opcje konsolidatora.

- Biblioteka DLL rozszerzenia MFC nie ma `CWinApp`-klasy pochodnej.

- Biblioteka DLL rozszerzenia MFC, musisz podać specjalny `DllMain`. Dostarcza przez kreatora AppWizard `DllMain` funkcji, które można zmodyfikować.

- Biblioteka DLL rozszerzenia MFC zapewniają zazwyczaj procedury inicjowania, aby utworzyć `CDynLinkLibrary` Jeśli rozszerzeń MFC DLL chce do wyeksportowania `CRuntimeClass`ak lub zasoby do aplikacji. Klasy pochodne `CDynLinkLibrary` mogą być używane, jeśli dane poszczególnych aplikacji musi być utrzymywana przez rozszerzenia MFC biblioteki DLL.

Te zagadnienia są opisane bardziej szczegółowo poniżej. Ponadto należy zapoznać się w próbce zaawansowanych koncepcji MFC [DLLHUSK](../visual-cpp-samples.md) , ponieważ zawiera ono:

- Tworzenie aplikacji przy użyciu biblioteki udostępnione. (DLLHUSK. Plik EXE jest aplikacja MFC, która łączy dynamicznie do biblioteki MFC dll, a także inne).

- Kompilowanie rozszerzenia MFC biblioteki DLL. (Należy pamiętać flagi specjalnych, takich jak `_AFXEXT` które są używane podczas tworzenia biblioteki DLL rozszerzenia MFC)

- Dwa przykłady biblioteki DLL rozszerzeń MFC. Pokazuje podstawowa struktura Biblioteka DLL rozszerzenia MFC z ograniczoną eksportu (TESTDLL1) i inne programy eksportowania całej klasy interfejsu (TESTDLL2).

Zarówno aplikacja klienta, jak i wszystkie biblioteki DLL rozszerzeń MFC, należy użyć tej samej wersji MFCxx.DLL. Należy Konwencją biblioteki MFC DLL i zapewnić zarówno debugowania i handlu detalicznego (/ release) w wersji z Twojego DLL rozszerzenia MFC. Pozwala to na programów klienckich do tworzenia wersji handlu detalicznego i debugowanie swoich aplikacji i łączą je z odpowiednich debugowania lub wersji detalicznej wszystkie biblioteki dll.

> [!NOTE]
>  Ponieważ C++ nazwę przekręcaniu i wyeksportować problemy, listę eksportu z biblioteki DLL rozszerzenia MFC może być różna debugowania, jak i sprzedaży detalicznej wersji tej samej biblioteki DLL i bibliotek DLL dla różnych platform. Handlu detalicznego MFCxx.DLL ma około 2000 wyeksportowane punkty wejścia; debugowanie MFCxxD.DLL ma około 3000 wyeksportowane punkty wejścia.

### <a name="quick-note-on-memory-management"></a>Szybką notatkę na zarządzanie pamięcią

Sekcję pod tytułem "Zarządzanie pamięcią," osiągnie koniec cyklu ta uwaga techniczna Opisuje implementację MFCxx.DLL udostępnionej wersja MFC. Informacje, których potrzebujesz, aby zaimplementować tylko rozszerzenia MFC biblioteki DLL jest opisana w tym miejscu.

MFCxx.DLL i wszystkie rozszerzone dll MFC ładowany do przestrzeni adresowej aplikacja kliencka użyje tych samych alokatora pamięci, ładowania zasobów i inne stany "global" MFC tak, jakby znajdowały się w tej samej aplikacji. Jest to znaczące, ponieważ biblioteki DLL bez MFC i zwykłych bibliotekach MFC dll, która statycznie łączy do MFC, czy dokładnym przeciwieństwem ale przydzielanie każdej biblioteki DLL z puli pamięci.

Jeśli biblioteka DLL rozszerzenia MFC przydziela pamięci, pamięci można swobodnie intermix z innym obiektem przydzielone aplikacji. Ponadto jeśli wystąpiła awaria aplikacji korzystającej z udostępnionej biblioteki MFC, ochronę systemu operacyjnego Obsługa integralności innych aplikacji MFC, udostępnianie biblioteki DLL.

Podobnie innych państw "global" MFC, takich jak bieżący plik wykonywalny można załadować zasobów, są również współużytkowane aplikacji klienckiej i wszystkie biblioteki DLL rozszerzeń MFC także MFCxx.DLL sam.

### <a name="building-an-mfc-extension-dll"></a>Kompilowanie rozszerzenia MFC biblioteki DLL

AppWizard umożliwia tworzenie projektu biblioteki DLL rozszerzeń MFC i automatycznie wygeneruje odpowiedni kompilatora i ustawienia konsolidatora. Było również wygenerować `DllMain` funkcji, które można zmodyfikować.

Jeśli konwertujesz istniejący projekt rozszerzenia MFC DLL, uruchom za pomocą standardowych reguł do tworzenia aplikacji przy użyciu udostępnionej wersja MFC, a następnie wykonaj następujące czynności:

- Dodaj **/D_AFXEXT** do flag kompilatora. W oknie dialogowym właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię preprocesora. Dodaj `_AFXEXT` do pola zdefiniowanie makra, oddzielając każdy z elementów średnikami.

- Usuń **/Gy** przełącznika kompilatora. W oknie dialogowym właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię generowania kodu. Upewnij się, że opcja "Włącz funkcję łączenia na poziomie" nie jest włączone. Ułatwi wyeksportować klasy, ponieważ konsolidator nie spowoduje usunięcia nieużywanych funkcji. Jeśli oryginalny projekt jest używany do tworzenia regularnych bibliotek DLL MFC połączone statycznie z MFC, zmiana **/MT [d]** opcji kompilatora **/MD [d]**.

- Tworzenie eksportu biblioteki w języku **/dll** opcję, aby łącza. Spowoduje to ustawienie podczas tworzenia nowy obiekt docelowy, określając Biblioteka dołączana dynamicznie Win32 jako typ docelowy.

### <a name="changing-your-header-files"></a>Zmiana pliki nagłówkowe

Celem rozszerzenia MFC biblioteki DLL jest zazwyczaj Eksportuj niektóre typowe funkcje do co najmniej jednej aplikacji, których możesz skorzystać z tej funkcji. To wrzała w dół do eksportowania klasy i funkcje globalne, które są dostępne dla aplikacji klienckich.

W tym celu należy upewnić się, że na każdej z tych funkcji elementu członkowskiego jest oznaczony jako importowania lub eksportowania zgodnie z potrzebami. Wymaga to specjalne deklaracje: `__declspec(dllexport)` i `__declspec(dllimport)`. Gdy Twoich zajęciach są używane przez aplikacje klienckie, mają być deklarowane jako `__declspec(dllimport)`. Podczas kompilowania rozszerzeń MFC DLL, sama powinien być zadeklarowany jako `__declspec(dllexport)`. Ponadto funkcje musi być faktycznie eksportowany, dzięki czemu programy klienckie powiązać je w czasie ładowania.

Aby eksportować całej klasy, należy użyć `AFX_EXT_CLASS` w definicji klasy. To makro jest zdefiniowana przez strukturę jako `__declspec(dllexport)` podczas `_AFXDLL` i `_AFXEXT` jest zdefiniowany, ale definiowane jako `__declspec(dllimport)` podczas `_AFXEXT` nie został zdefiniowany. `_AFXEXT` zgodnie z powyższym opisem jest zdefiniowana tylko podczas kompilowania rozszerzenia MFC biblioteki DLL. Na przykład:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Eksportowanie nie całej klasy

Czasami można wyeksportować tylko poszczególne niezbędnych członków klasy. Na przykład jeśli eksportujesz `CDialog`-klasy pochodne mogą tylko należy wyeksportować konstruktora i `DoModal` wywołania. Możesz wyeksportować te elementy członkowskie przy użyciu biblioteki DLL. Plik DEF, ale można również użyć `AFX_EXT_CLASS` w podobny sposób na poszczególnych elementów członkowskich, należy wyeksportować.

Na przykład:

```cpp
class CExampleDialog : public CDialog
{
public:
    AFX_EXT_CLASS CExampleDialog();
    AFX_EXT_CLASS int DoModal();
    // rest of class definition
    // ...
};
```

Gdy to zrobisz, może wystąpić problem dodatkowe ponieważ wszystkie elementy członkowskie klasy nie są eksportowane. Problem jest w ten sposób współpracujące makr MFC. Zadeklaruj kilka makra pomocnika MFC faktycznie lub zdefiniować elementy członkowskie danych. Dlatego te elementy członkowskie danych będzie również trzeba wyeksportować z biblioteki DLL.

Na przykład DECLARE_DYNAMIC — makro jest zdefiniowany następująco, podczas kompilowania rozszerzenia MFC biblioteki DLL:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \

```

Wiersz zaczynający "statyczne `AFX_DATA`" jest deklarowania obiektu statycznego wewnątrz klasy. Aby poprawnie eksportu tej klasy i uzyskać dostęp do informacji środowisko uruchomieniowe z klienta. Plik EXE, należy wyeksportować tego obiektu statycznego. Ponieważ obiektu statycznego jest zadeklarowana za pomocą modyfikatora `AFX_DATA`, musisz zdefiniować `AFX_DATA` jako `__declspec(dllexport)` podczas kompilowania biblioteki DLL i zdefiniuj go w formie `__declspec(dllimport)` podczas kompilowania pliku wykonywalnego klienta.

Jak wspomniano powyżej, `AFX_EXT_CLASS` jest już zdefiniowany w ten sposób. Wystarczy ponownie zdefiniować `AFX_DATA` być taka sama jak `AFX_EXT_CLASS` wokół swojej definicji klasy.

Na przykład:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS
class CExampleView : public CView
{
    DECLARE_DYNAMIC()
    // ... class definition ...
};
#undef  AFX_DATA
#define AFX_DATA
```

Zawsze używa MFC `AFX_DATA` symboli dla elementów danych definiuje w makrach, więc ta metoda będzie działać w przypadku takich scenariuszy. Na przykład będzie działać DECLARE_MESSAGE_MAP.

> [!NOTE]
> Jeśli eksportujesz całej klasy, a nie wybrane elementy członkowskie klasy automatycznie eksportowane są statyczne elementy członkowskie danych.

Można użyć tej samej techniki, automatycznie eksportowania `CArchive` operator wyodrębniania dla klas, które używają DECLARE_SERIAL i IMPLEMENT_SERIAL makr. Wyeksportuj operator archiwum, nawiasy w deklaracji klasy (na terenie. Plik H) z następującym kodem:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-afxext"></a>Ograniczenia _afxext —

Możesz użyć _**AFXEXT** symbol wstępnego procesora dla rozszerzenia MFC biblioteki DLL tak długo, ponieważ nie masz wiele warstw biblioteki DLL rozszerzeń MFC. Jeśli masz rozszerzenia MFC biblioteki dll, takich jak wywoływanie lub pochodzić od klasy własne rozszerzenia MFC biblioteki dll, które następnie pochodzić od klasy MFC, musi użyć symbol preprocesora Aby uniknąć niejednoznaczności.

Problem polega na tym w Win32, należy jawnie deklarować, że wszystkie dane jako `__declspec(dllexport)` jeśli mają zostać wyeksportowane z biblioteki DLL, a `__declspec(dllimport)` przypadku ma zostać zaimportowany z biblioteki DLL. Podczas definiowania `_AFXEXT`, nagłówki MFC, upewnij się, że `AFX_EXT_CLASS` jest poprawnie zdefiniowany.

Jeśli masz wiele warstw, jeden symbol taki jak `AFX_EXT_CLASS` nie wystarcza, ponieważ rozszerzenia MFC biblioteki DLL mogą być eksportowanie nowych klas, a także importowanie innych klas z innej biblioteki DLL rozszerzenia MFC. Aby poradzić sobie z tym problemem, należy użyć specjalnego symbol preprocesora, który wskazuje, czy tworzysz DLL w przeciwieństwie do użycia biblioteki DLL. Załóżmy, że dwie biblioteki DLL rozszerzeń MFC, A.DLL i B.DLL. Niektóre klasy w A.H i B.H, ich eksportowanie odpowiednio. B.DLL korzysta z klas z A.DLL. Pliki nagłówkowe będą wyglądać mniej więcej tak:

```cpp
/* A.H */
#ifdef A_IMPL
    #define CLASS_DECL_A   __declspec(dllexport)
#else
    #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ /* ... class definition ... */ };

/* B.H */
#ifdef B_IMPL
    #define CLASS_DECL_B   __declspec(dllexport)
#else
    #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ /* ... class definition ... */ };
```

Podczas kompilowania A.DLL bazuje na **/DA_IMPL** i podczas kompilowania B.DLL jest zbudowany z **/DB_IMPL**. Za pomocą osobnych symbole dla każdej biblioteki DLL, CExampleB są eksportowane i CExampleA jest importowany podczas kompilowania B.DLL. CExampleA jest wyeksportowany podczas tworzenia A.DLL i zaimportować, gdy jest używana przez B.DLL (lub innego klienta).

Nie można wykonać tego rodzaju warstw, korzystając z wbudowanej `AFX_EXT_CLASS` i `_AFXEXT` symboli preprocesora. Opisaną technikę rozwiązuje ten problem, w sposób nie w przeciwieństwie do mechanizmu MFC sam używa podczas tworzenia jej OLE, bazy danych i sieci MFC biblioteki DLL rozszerzeń.

### <a name="not-exporting-the-entire-class"></a>Eksportowanie nie całej klasy

Ponownie należy zwrócić szczególną uwagę podczas całej klasy nie są eksportowane. Należy upewnić się, poprawnie wyeksportowane elementów niezbędnych danych, utworzonych przez makr MFC. Można to zrobić przez ponowne zdefiniowanie `AFX_DATA` makra z określonej klasy. Należy to określić ilekroć całej klasy nie są eksportowane.

Na przykład:

```cpp
// A.H
#ifdef A_IMPL
    #define CLASS_DECL_A  _declspec(dllexport)
#else
    #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
    DECLARE_DYNAMIC()
    CLASS_DECL_A int SomeFunction();
    // class definition
    // ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="dllmain"></a>DllMain

Poniżej znajduje się dokładnie kod, który należy umieścić w pliku głównym źródłem dla rozszerzenia MFC biblioteki DLL. Pochodziły po zawiera standardowe. Należy pamiętać, że użycie przez kreatora AppWizard do tworzenia modułu uruchamiającego plików dla rozszerzeń MFC DLL, dostarcza mu `DllMain` dla Ciebie.

```cpp
#include "afxdllx.h"

static AFX_EXTENSION_MODULE extensionDLL;

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      // MFC extension DLL one-time initialization
      if (!AfxInitExtensionModule(
             extensionDLL, hInstance))
         return 0;

      // TODO: perform other initialization tasks here
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      // MFC extension DLL per-process termination
      AfxTermExtensionModule(extensionDLL);

      // TODO: perform other cleanup tasks here
   }
   return 1;   // ok
}
```

Wywołanie `AfxInitExtensionModule` przechwytuje klasy środowiska wykonawczego modułów (`CRuntimeClass` struktury) oraz jego fabryk obiektu (`COleObjectFactory` obiektów) do użycia po późniejszym `CDynLinkLibrary` obiekt zostanie utworzony. (Opcjonalnie) wywołanie `AfxTermExtensionModule` umożliwia MFC do oczyszczania biblioteki DLL rozszerzenia MFC podczas każdego procesu odłącza (której się dzieje, gdy kończy proces lub zwalnianie biblioteki DLL na `FreeLibrary` wywołania) z biblioteki DLL rozszerzenia MFC. Ponieważ większość rozszerzenia MFC biblioteki DLL nie są ładowane dynamicznie (zazwyczaj są połączone za pośrednictwem ich bibliotekami importowanymi), wywołanie `AfxTermExtensionModule` zazwyczaj nie jest konieczne.

Jeśli aplikacja ładuje i zwalnia dynamicznie biblioteki DLL rozszerzeń MFC, należy wywołać `AfxTermExtensionModule` jak pokazano powyżej. Należy również użyć `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 `LoadLibrary` i `FreeLibrary`) Jeśli aplikacja korzysta z wielu wątków lub dynamicznie ładuje rozszerzenia MFC biblioteki DLL. Za pomocą `AfxLoadLibrary` i `AfxFreeLibrary` ubezpieczycielom, uruchamiania i zamykania kod, który wykonuje, gdy rozszerzenia MFC biblioteki DLL jest ładowany i zwolnione nie doprowadzić do uszkodzenia globalne MFC.

Plik nagłówkowy AFXDLLX. H zawiera specjalne definicje struktury używanych w bibliotek DLL rozszerzeń MFC, takich jak definicja `AFX_EXTENSION_MODULE` i `CDynLinkLibrary`.

Globalna *extensionDLL* musi być zadeklarowany, jak pokazano. W przeciwieństwie do 16-bitową wersję biblioteki MFC można przydzielić pamięci i wywoływać funkcje MFC w tym czasie, ponieważ MFCxx.DLL jest w pełni zainicjowany przez czas Twojej `DllMain` jest wywoływana.

### <a name="sharing-resources-and-classes"></a>Udostępnianie zasobów i klas

Proste bibliotek DLL rozszerzeń MFC należy eksportować tylko kilka funkcji o niskiej przepustowości do aplikacji klienckiej i od niczego więcej. Więcej bibliotek DLL intensywnie korzystających z interfejsu użytkownika może chcieć wyeksportować klasy języka C++ i zasoby do aplikacji klienckiej.

Eksportowanie zasobów odbywa się za pośrednictwem listy zasobów. W każdej aplikacji jest pojedynczo połączoną listą `CDynLinkLibrary` obiektów. Podczas wyszukiwania zasobu, większość standardowych implementacji MFC, które ładowanie zasobów przyjrzeć bieżącego modułu zasobów (`AfxGetResourceHandle`) i nie można odnaleźć przeszukiwania, gdy lista `CDynLinkLibrary` obiekty z próby załadowania żądanego zasobu.

Dynamiczne tworzenie obiektów C++ podana nazwa klasy języka C++ jest podobny. Mechanizm deserializacji obiektu MFC musi mieć wszystkie `CRuntimeClass` obiekty zarejestrowane tak, aby go odtworzyć za dynamiczne tworzenie obiektu języka C++ typu wymagane oparte na co wcześniej została zapisana.

Jeśli chcesz, aby aplikacja kliencka, aby użyć klasy w rozszerzeniu MFC DLL, które są `DECLARE_SERIAL`, a następnie należy wyeksportować w Twoich zajęciach, które mają być widoczne dla aplikacji klienckiej. To również odbywa się przez zalet `CDynLinkLibrary` listy.

W przypadku próbce zaawansowanych koncepcji MFC [DLLHUSK](../visual-cpp-samples.md), listy wygląda mniej więcej tak:

```Example
head ->   DLLHUSK.EXE   - or - DLLHUSK.EXE
               |                    |
          TESTDLL2.DLL         TESTDLL2.DLL
               |                    |
          TESTDLL1.DLL         TESTDLL1.DLL
               |                    |
               |                    |
           MFC90D.DLL           MFC90.DLL
```

MFCxx.DLL jest zwykle ostatni zasób i lista klas. MFCxx.DLL obejmuje wszystkie standardowe zasoby MFC, w tym monitu ciągi dla identyfikatorów poleceń standardowych. Umieszczając go na końcu listy umożliwia bibliotek DLL i aplikacja kliencka nie mają własnej kopii standardowe zasoby MFC, ale można polegać na zasoby udostępnione w MFCxx.DLL zamiast tego.

Scalanie zasobów i nazwy klasy wszystkie biblioteki dll w przestrzeni nazw aplikacji klienta ma wadą przeznaczonego do należy zachować ostrożność, jakie identyfikatory lub nazwy, które można wybrać. Można oczywiście tę funkcję można wyłączyć przez nie wyeksportowanie albo zasobów lub `CDynLinkLibrary` obiektu do aplikacji klienckiej. [DLLHUSK](../visual-cpp-samples.md) przykładowe zarządza przestrzeń nazw udostępnionych zasobów przy użyciu wiele plików nagłówkowych. Zobacz [techniczne 35 Uwaga](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) więcej porad na temat korzystania z plików udostępnionych zasobów.

### <a name="initializing-the-dll"></a>Inicjowanie biblioteki DLL

Jak wspomniano powyżej, zazwyczaj należy utworzyć `CDynLinkLibrary` obiektu, aby wyeksportować klasy i zasoby do aplikacji klienckiej. Należy podać wyeksportowano punkt wejścia do zainicjowania biblioteki DLL. Co najmniej to void procedurę, która nie przyjmuje żadnych argumentów i zwraca wartość nothing, ale można nadać dowolną.

Jeśli używasz tego podejścia, każdej aplikacji klienta, który chce użyć biblioteki DLL musi wywołać ta procedura inicjowania. Może również przydzielić to `CDynLinkLibrary` obiektu w swojej `DllMain` tylko po wywołaniu `AfxInitExtensionModule`.

Procedura inicjowania, należy utworzyć `CDynLinkLibrary` obiekt sterty bieżącej aplikacji, powiązaną rozszerzenia MFC biblioteki DLL informacji. Można to zrobić przy użyciu następujących czynności:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Nazwa procedury *InitXxxDLL* w tym przykładzie, może być dowolną. Musi być **extern "C"**, ale wykonanie sprawia, że tak, Eksportuj listę łatwiejszy w utrzymaniu.

> [!NOTE]
> Jeśli używasz rozszerzenia MFC biblioteki DLL od zwykłej biblioteki MFC DLL, należy wyeksportować tę funkcję inicjowania. Ta funkcja musi być wywołana z zwykłej biblioteki MFC DLL przed użyciem dowolnej klasy biblioteki DLL rozszerzeń MFC lub zasobów.

### <a name="exporting-entries"></a>Eksportowanie wpisów

Prosty sposób wyeksportować swojej klasy jest użycie `__declspec(dllimport)` i `__declspec(dllexport)` dla każdej klasy, a funkcja globalna, które chcesz wyeksportować. To sprawia, że o wiele prostsze, ale jest mniej wydajne niż nazewnictwa każdego punktu wejścia (opisanych poniżej), ponieważ ma mniejszą kontrolę nad jakie funkcje są eksportowane i nie można wyeksportować funkcje według liczby porządkowej. TESTDLL1 i TESTDLL2 używają tej metody, aby wyeksportować ich wpisów.

Bardziej efektywną metodę (i metodę używaną przez MFCxx.DLL) nie jest eksportowane każdego wpisu ręcznie za pomocą nazw każdy wpis. Plik DEF. Ponieważ firma Microsoft są eksportowane selektywne eksporty z naszych biblioteki DLL (oznacza to nie wszystko), firma Microsoft należy zdecydować, interfejsy, które szczególności przywołamy do wyeksportowania. Jest to trudne, ponieważ zniekształcone nazwy do konsolidatora należy określić w postaci wpisów. Plik DEF. Nie należy eksportować wszystkie klasy C++, chyba że potrzebujesz tak naprawdę mieć łącza symbolicznego.

Po wypróbowaniu eksportowanie C++ klasy za pomocą. DEF pliku przed może zajść potrzeba Opracuj narzędzie do automatycznego wygenerowania tej listy. Można to zrobić za pomocą łącza dwuetapowego procesu. Link biblioteki DLL raz przy użyciu eksportuje żadnych danych i umożliwić konsolidator generuje. Plik mapy. . Plik mapy może służyć do generowania listy funkcji, które powinny być eksportowane, więc z niektórych rozmieszczanie może służyć do generowania wpisów Eksport do usługi. Plik DEF. Na liście eksportu dla MFCxx.DLL, OLE i bibliotek DLL rozszerzeń MFC bazy danych, kilka tysięcy w polu numer został wygenerowany za pomocą takiego procesu (mimo że nie jest całkowicie automatyczny i wymaga niektóre strony dostosowywania każdego raz pewnego).

### <a name="cwinapp-vs-cdynlinklibrary"></a>Klasa CWinApp programu vs. CDynLinkLibrary

Biblioteka DLL rozszerzenia MFC nie ma `CWinApp`-pochodnych własnego obiektu; zamiast tego muszą współpracować z `CWinApp`-pochodzi obiekt aplikacji klienckiej. Oznacza to, czy aplikacja kliencka jest właścicielem pompy komunikatów głównym, wykonywania pętli bezczynności i tak dalej.

Jeśli biblioteka DLL rozszerzenia MFC musi obsługiwać dodatkowe dane dla każdej aplikacji, można uzyskać nowe klasy z `CDynLinkLibrary` i utwórz go w InitXxxDLL procedurze opisano powyżej. Podczas uruchamiania, biblioteki DLL, można sprawdzić listę bieżącej aplikacji `CDynLinkLibrary` obiektu do znalezienia dla tego określonego rozszerzenia MFC biblioteki DLL.

### <a name="using-resources-in-your-dll-implementation"></a>Korzystanie z zasobów w danej implementacji biblioteki DLL

Jak wspomniano powyżej, ładowanie zasobów domyślne przeprowadzi listy `CDynLinkLibrary` obiektów szukasz pierwszy plik EXE lub DLL, która ma żądanego zasobu. Wszystkie interfejsy API biblioteki MFC, a także wszystkich wewnętrznych kod używa `AfxFindResourceHandle` zaprezentuje na liście zasobów można znaleźć żadnych zasobów, niezależnie od tego, gdzie mogą znajdować się.

Jeśli chcesz tylko ładowanie zasobów w określonym miejscu przy użyciu interfejsów API `AfxGetResourceHandle` i `AfxSetResourceHandle` zapisać stary dojścia i ustaw nowy uchwyt. Pamiętaj przywrócić stare dojście do zasobu, aby powrócić do aplikacji klienckiej. Przykładowe TESTDLL2 używa tego podejścia do jawnie ładowania menu.

Zalet listy ma wad jest wolniejsze i wymaga zarządzania zakresami identyfikator zasobu. Ma tę zaletę, że aplikacja kliencka, który stanowi łącze do kilku bibliotek DLL rozszerzeń MFC można użyć dowolnego zasobu dostarczone przez bibliotekę DLL bez konieczności określania dojście wystąpienia biblioteki DLL. `AfxFindResourceHandle` Interfejs API służy do zalet listy zasobów do wyszukania danego dopasowania. Ona przyjmuje nazwę i typ zasobu i zwraca wartość, gdzie najpierw został znaleziony dojście do zasobu (lub wartość NULL).

##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a> Pisząc aplikację, która korzysta z wersji biblioteki DLL

### <a name="application-requirements"></a>Wymagania dotyczące aplikacji

Aplikacja, która korzysta z udostępnionej wersja MFC, należy wykonać kilka prostych reguł:

- Musi on mieć `CWinApp` obiektu i obowiązują standardowe reguły "pompy komunikatów".

- Musi być skompilowana przy użyciu zestawu flag wymagany kompilator (patrz poniżej).

- Należy go połączyć z bibliotekami importowanymi MFCxx. Przez ustawienie flagi wymagane kompilatora, nagłówki MFC określić w czasie połączenia biblioteki, która aplikacja ma się łączyć z.

- Aby uruchomić plik wykonywalny, MFCxx.DLL musi być w ścieżce lub w katalogu systemu Windows.

### <a name="building-with-the-development-environment"></a>Kompilowanie przy użyciu środowiska programistycznego

Jeśli używasz wewnętrznej pliku reguł programu make z większością standardowych wartościach domyślnych, można łatwo zmienić projekt do kompilacji wersji biblioteki DLL.

Następny krok przyjęto założenie, że masz prawidłowego działania aplikacji MFC połączone z NAFXCWD. LIB (dla debug) i NAFXCW. LIB (dla handlu detalicznego) i chcesz przekonwertować go pod kątem używają udostępnionych wersji biblioteki MFC. Używasz środowiska Visual C++ i istnieje plik projektu wewnętrznego.

1. Na **projektów** menu, kliknij przycisk **właściwości**. W **ogólne** strony w obszarze **domyślne wartości projektu**, ustaw Microsoft Foundation Classes **Użyj MFC w współdzielonej bibliotece DLL** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Kompilowanie z użyciem NMAKE

Jeśli jest używana funkcja zewnętrznego pliku reguł programu make Visual c++ lub korzystania z NMAKE bezpośrednio, należy edytować Twojego pliku reguł programu make do obsługi kompilatora i opcje konsolidatora

Flagi kompilatora wymagane:

- **/ / MD D_AFXDLL**
   **/D_AFXDLL**

Standardowe nagłówki MFC należy ten symbol do zdefiniowania:

- **/ MD** aplikacja musi używać wersji DLL biblioteki wykonawczej języka C

Wszystkie inne flagi kompilatora postępuj zgodnie z ustawień domyślnych MFC (na przykład _DEBUG do debugowania).

Edytuj konsolidatora listę bibliotek. Zmiana NAFXCWD. LIB do MFCxxD.LIB i zmień NAFXCW. W bibliotece statycznej LIB MFCxx.LIB. Zastąp LIBC. LIB, za pomocą MSVCRT. LIB. Inne biblioteki MFC jest ważne, czy jest umieszczony MFCxxD.LIB **przed** żadnych bibliotek C runtime.

Opcjonalnie dodaj **/D_AFXDLL** do obu handlu detalicznego i debugowania opcji kompilatora zasobów (ten, który kompiluje faktycznie zasobów przy użyciu **/R**). Dzięki temu końcowego pliku wykonywalnego mniejszych dzięki udostępnieniu zasobów, które znajdują się w biblioteki MFC DLL.

Pełną rekompilację jest wymagany po wprowadzeniu tych zmian.

### <a name="building-the-samples"></a>Kompilowanie przykładów programu

Większość przykładowych programów MFC mogą być wbudowane z Visual C++ lub udostępnionego zgodnego z NMAKE pliku reguł programu MAKE w wierszu polecenia.

Aby przekonwertować żadnego z tych przykładów, aby użyć MFCxx.DLL, można załadować. Klucz MAK pliku w Visual C++ i ustaw opcje projektu, zgodnie z powyższym opisem. Jeśli używasz kompilacji NMAKE, można określić "AFXDLL = 1" w NMAKE wiersz polecenia i który będzie skompilować przykład za pomocą udostępnionej biblioteki MFC.

W próbce zaawansowanych koncepcji MFC [DLLHUSK](../visual-cpp-samples.md) został utworzony za pomocą wersja dll biblioteki MFC. W tym przykładzie nie tylko przedstawiono sposób kompilowania aplikacji połączonej z MFCxx.DLL, ale również dwie inne funkcje opcji pakowania biblioteki MFC DLL, takich jak opisane w dalszej części tego Uwaga techniczna bibliotek DLL rozszerzeń MFC.

### <a name="packaging-notes"></a>Uwagi dotyczące tworzenia pakietów

Na wersję detaliczną biblioteki dll (MFCxx [U]. Biblioteka DLL) można dowolnie rozprowadzać. Wersja do debugowania biblioteki DLL nie można dowolnie rozprowadzać i należy używać tylko podczas programowania aplikacji.

Debugowanie bibliotek DLL są dostarczane z informacji o debugowaniu. Za pomocą debugera programu Visual C++, można śledzić wykonywanie aplikacji, a także biblioteki DLL. Wersja biblioteki dll (MFCxx [U]. Biblioteka DLL) nie zawiera informacji o debugowaniu.

Dostosowywanie lub ponownie skompiluj biblioteki dll, następnie należy wywołać ich coś innego niż plik "MFCxx" SRC MFC MFCDLL. Klucz MAK w tym artykule opisano opcje kompilacji i zawiera logikę zmiana nazwy biblioteki DLL. Zmiana nazw plików jest to konieczne, ponieważ te biblioteki DLL są potencjalnie współużytkowane przez wiele aplikacji MFC. Posiadanie niestandardowej wersji biblioteki MFC DLL zamiany zainstalowanych w systemie mogą przestać działać inna aplikacja MFC przy użyciu udostępnionej biblioteki MFC DLL.

Nie zaleca się odbudowanie biblioteki MFC DLL.

##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a> Jak zaimplementowano MFCxx.DLL

W poniższej sekcji opisano sposób implementacji MFC DLL (MFCxx.DLL i MFCxxD.DLL). Szczegóły tutaj również nie są istotne, jeśli wszystkie co chcesz zrobić jest zrozumienie biblioteki MFC DLL za pomocą aplikacji. Szczegółowe informacje w tym miejscu nie są istotne dla zrozumienia, jak pisać rozszerzenia MFC biblioteki DLL, ale opis tej implementacji może pomóc w pisaniu własne biblioteki DLL.

### <a name="implementation-overview"></a>Przegląd wdrożenia

Biblioteki MFC DLL tak naprawdę jest przypadkiem szczególnym Biblioteka DLL rozszerzenia MFC, zgodnie z powyższym opisem. Ma on bardzo dużej liczby eksportów dla dużej liczby klas. Istnieje kilka dodatkowych rzeczy, które robimy biblioteki MFC dll, które ułatwiają jeszcze bardziej specjalne niż regularne biblioteki DLL rozszerzenia MFC.

### <a name="win32-does-most-of-the-work"></a>Win32 wykonuje większość pracy

16-bitowej wersji MFC potrzebne kilka technik specjalne, włącznie z danymi dla aplikacji w segmencie stosu segmentów specjalne utworzone przez jakiś kod zestawu 80 x 86, kontekst wyjątku na proces i innych technik. Win32 bezpośrednio obsługuje na przetwarzanie danych w bibliotece DLL, która ma większość czasu. W większości przypadków MFCxx.DLL jest po prostu NAFXCW. Lib — zapakowane w bibliotece DLL. Jeśli spojrzysz na kod źródłowy biblioteki MFC, znajdują się bardzo niewiele _AFXDLL #ifdef, ponieważ istnieją w bardzo nielicznych przypadkach specjalne, które należy podjąć. Specjalne przypadki, które są specjalnie do czynienia z Win32 na Windows 3.1 (zwanej także systemach Win32). Systemach Win32 nie nie-process DLL dane o pomocy technicznej bezpośrednio więc biblioteki MFC DLL, należy użyć lokalny magazyn wątków (TLS) interfejsy API Win32 w celu uzyskania przetwarzanie danych lokalnych.

### <a name="impact-on-library-sources-additional-files"></a>Wpływ na bibliotece źródeł, dodatkowe pliki

Wpływ **_AFXDLL** wersja na normalne źródła biblioteki klas MFC i nagłówków jest relatywnie. Istnieje plik specjalnej wersji (AFXV_DLL. Godz.), a także plik nagłówkowy dodatkowe (AFXDLL_. H) zawarte AFXWIN głównego. Nagłówek H. AFXDLL_. Nagłówek H `CDynLinkLibrary` klasy i inne szczegóły implementacji obu `_AFXDLL` aplikacji i bibliotek DLL rozszerzeń MFC. AFXDLLX. H nagłówka znajduje się do tworzenia bibliotek DLL rozszerzeń MFC (zobacz wyżej, aby uzyskać szczegółowe informacje).

Regularne źródeł do biblioteki MFC w MFC SRC ma dodatkowy kod warunkowe w obszarze `_AFXDLL` #ifdef. Plik źródłowy dodatkowe (DLLINIT. CPP) zawiera dodatkowy kod inicjalizacji biblioteki DLL i innych klej do udostępnionej wersja MFC.

Aby można było utworzyć udostępnionej wersja MFC, znajdują się dodatkowe pliki. (Zobacz poniżej szczegółowe informacje dotyczące sposobu tworzenia pliku DLL).

- Dwa. Pliki DEF służą do eksportowania biblioteki MFC DLL punkty wejścia do debugowania (MFCxxD.DEF) i wersje (MFCxx.DEF) biblioteki dll.

- . Plik RC (MFCDLL. RC) zawiera wszystkie standardowe zasoby MFC i zasób VERSIONINFO dla biblioteki DLL.

- ELEMENT. Plik CLW (MFCDLL. CLW) jest dostarczany, aby zezwolić na przeglądanie MFC klasy przy użyciu ClassWizard. Uwaga: Ta funkcja nie jest na wersja dll biblioteki MFC.

### <a name="memory-management"></a>Zarządzanie pamięcią

Aplikację przy użyciu MFCxx.DLL korzysta z wspólnego alokatora pamięci, dostarczone przez MSVCRTxx.DLL, współdzielonej bibliotece DLL środowiska uruchomieniowego C. Aplikacji i wszystkie biblioteki DLL rozszerzeń MFC, a także same biblioteki MFC DLL użyć tego alokatora pamięci współdzielonej. Za pomocą współdzielonej bibliotece DLL dla alokacji pamięci, biblioteki MFC DLL można przydzielić pamięci, który później zostanie zwolniony przez aplikację lub na odwrót. Ponieważ zarówno aplikacja, jak i biblioteki DLL, musisz użyć tego samego programu przydzielania, nie powinien przesłonić globalny C++ **nowy operator** lub **operatora delete**. Te same reguły dotyczą pozostałą część procedur alokacji pamięci środowiska wykonawczego języka C (takie jak **— funkcja malloc**, **realloc**, **bezpłatne**i inne).

### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Liczby porządkowe i __declspec(dllexport) klasy i nazwy biblioteki DLL

Nie używamy `class` **__declspec(dllexport)** funkcje kompilatora języka C++. Zamiast tego lista eksportu jest oferowana źródeł biblioteki klas (MFCxx.DEF i MFCxxD.DEF). Tylko te wybranego zestawu punktów wejścia (funkcje i dane) są eksportowane. Inne symbole, takie jak MFC prywatnej implementacji funkcji lub klasy, nie są eksportowane wszystkich eksporty są wykonywane według numeru porządkowego bez nazwy ciągu w tabeli rezydentnego lub niemający nazwy.

Za pomocą `class` **__declspec(dllexport)** może być wartą rozważenia alternatywą dla tworzenia bibliotek DLL mniejszy, ale w przypadku dużych biblioteki DLL, takie jak MFC, domyślny mechanizm eksportu ma wydajność i pojemność limitów.

Co to oznacza, że wszystkie jest firma Microsoft spakować dużej liczby funkcji w wersji MFCxx.DLL, który jest tylko około 800 KB bez uszczerbku dla dużej ilości wykonywania i szybkość ładowania. MFCxx.DLL byłby 100 tysięcy większych ta technika nie była używana. Ponadto dzięki temu można dodać dodatkowe punkty wejścia na końcu. Plik DEF, która umożliwia proste przechowywanie wersji bez uszczerbku dla wydajności szybkości i rozmiaru eksportowania według liczby porządkowej. Wersja główna poprawki w bibliotece klas MFC zmieni nazwę biblioteki. Oznacza to, że MFC30. Biblioteka DLL jest redystrybucyjne biblioteki DLL zawierającą wersję 3.0 Biblioteka klas MFC. Uaktualnienie tę bibliotekę DLL powiedzieć w hipotetyczny 3.1 MFC DLL będą miały postać MFC31. Biblioteka DLL zamiast tego. Jeśli zmodyfikujesz kod źródłowy MFC, aby utworzyć niestandardową wersję biblioteki MFC DLL, użyj innej nazwy (i najlepiej bez "MFC" w nazwie).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
