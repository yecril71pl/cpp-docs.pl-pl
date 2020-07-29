---
title: 'TN033: wersja DLL biblioteki MFC'
ms.date: 06/28/2018
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
ms.openlocfilehash: c627f891efc893f4eb8dae4bfb0b3b78f7af1a46
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215936"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: wersja DLL biblioteki MFC

Ta Uwaga opisuje, jak można użyć MFCxx.DLL i MFCxxD.DLL (gdzie x jest numerem wersji MFC) udostępnionych bibliotek dołączanych dynamicznie z aplikacjami MFC i bibliotekami DLL rozszerzenia MFC. Aby uzyskać więcej informacji na temat zwykłych bibliotek MFC DLL, zobacz [Używanie MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Ta Uwaga techniczna dotyczy trzech aspektów bibliotek DLL. Ostatnie dwa są przeznaczone dla bardziej zaawansowanych użytkowników:

- [Jak utworzyć bibliotekę DLL rozszerzenia MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Jak skompilować aplikację MFC, która korzysta z biblioteki DLL w wersji MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Jak są implementowane udostępnione biblioteki DLL MFC](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Jeśli interesuje Cię Kompilowanie biblioteki DLL przy użyciu biblioteki MFC, która może być używana z aplikacjami nienależącymi do MFC (jest to zwykła Biblioteka MFC DLL), zapoznaj się z [uwagą techniczną 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Omówienie obsługi MFCxx.DLL: Terminologia i pliki

**Zwykła Biblioteka DLL MFC**: używasz zwykłej biblioteki MFC DLL do tworzenia autonomicznej biblioteki DLL przy użyciu niektórych klas MFC. Interfejsy w ramach granicy App/DLL są interfejsami "C", a aplikacja kliencka nie musi być aplikacją MFC.

Jest to wersja obsługująca biblioteki DLL obsługiwana w MFC 1,0. Jest on opisany w [uwagi technicznej 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) i zaawansowane przykłady pojęć MFC [DLLScreenCap](../overview/visual-cpp-samples.md).

> [!NOTE]
> Począwszy od Visual C++ w wersji 4,0, termin **USRDLL** jest przestarzały i został zastąpiony przez ZWYKŁĄ bibliotekę MFC DLL, która statycznie łączy się z MFC. Możesz również utworzyć zwykłą bibliotekę MFC DLL, która łączy dynamicznie z MFC.

MFC 3,0 (i nowsze) obsługuje regularne biblioteki MFC DLL ze wszystkimi nowymi funkcjami, takimi jak klasy OLE i bazy danych.

**AFXDLL**: jest również określana jako udostępniona wersja bibliotek MFC. Jest to nowa obsługa bibliotek DLL dodana w MFC 2,0. Sama Biblioteka MFC znajduje się w szeregu bibliotek DLL (opisanych poniżej), a aplikacja kliencka lub biblioteka DLL dynamicznie łączy biblioteki DLL, których to wymaga. Interfejsy w ramach granicy Application/DLL są interfejsami klas C++/MFC. Aplikacja kliencka musi być aplikacją MFC. Obsługuje ona wszystkie funkcje MFC 3,0 (wyjątek: kod UNICODE nie jest obsługiwany w przypadku klas baz danych).

> [!NOTE]
> Począwszy od Visual C++ w wersji 4,0, ten typ biblioteki DLL jest określany jako "Biblioteka DLL rozszerzenia".

Ta Uwaga będzie używać MFCxx.DLL do odwoływania się do całego zestawu MFC DLL, który obejmuje:

- Debuguj: MFCxxD.DLL (łącznie) i MFCSxxD. LIB (static).

- Wydanie: MFCxx.DLL (łącznie) i MFCSxx. LIB (static).

- Debugowanie Unicode: MFCxxUD.DLL (łącznie) i MFCSxxD. LIB (static).

- Wydanie Unicode: MFCxxU.DLL (łącznie) i MFCSxxU. LIB (static).

> [!NOTE]
> MFCSxx [U] [D]. Biblioteki LIB są używane w połączeniu z udostępnionymi bibliotekami DLL MFC. Biblioteki te zawierają kod, który musi być statycznie połączony z aplikacją lub biblioteką DLL.

Aplikacja łączy się z odpowiednimi bibliotekami importu:

- Debuguj: MFCxxD. LIB

- Wydanie: MFCxx. LIB

- Debugowanie Unicode: MFCxxUD. LIB

- Wersja Unicode: MFCxxU. LIB

"Biblioteka DLL rozszerzenia MFC" to biblioteka DLL oparta na MFCxx.DLL (i/lub innych udostępnionych bibliotekach DLL MFC). W tym miejscu Architektura składników MFC jest uruchamiana w. Jeśli klasa jest użyteczna z klasy MFC lub kompiluje inny zestaw narzędzi do MFC, można umieścić go w bibliotece DLL. Ta biblioteka DLL używa MFCxx.DLL, podobnie jak ostateczna aplikacja kliencka. Pozwala to na używanie klas liści wielokrotnego użytku, klas bazowych wielokrotnego użytku oraz klas widoku/dokumentu wielokrotnego użytku.

## <a name="pros-and-cons"></a>Specjaliści i wady

Dlaczego należy używać udostępnionej wersji biblioteki MFC

- Użycie biblioteki udostępnionej może spowodować mniejsze aplikacje (minimalna aplikacja, która używa większości biblioteki MFC, jest mniejsza niż 10 tys.).

- Udostępniona wersja MFC obsługuje biblioteki DLL rozszerzeń MFC i zwykłych bibliotek DLL MFC.

- Kompilowanie aplikacji wykorzystującej udostępnione biblioteki MFC jest szybsze niż tworzenie statycznie połączonej aplikacji MFC, ponieważ nie jest to konieczne do łączenia MFC. Jest to szczególnie prawdziwe w kompilacjach **debugowania** , gdzie konsolidator musi kompaktować informacje debugowania — przez połączenie z biblioteką DLL, która zawiera już informacje o debugowaniu, aby kompaktować aplikację.

Dlaczego nie należy używać udostępnionej wersji biblioteki MFC:

- Wysyłka aplikacji korzystającej z biblioteki udostępnionej wymaga dostarczania biblioteki MFCxx.DLL (i innych) razem z programem. MFCxx.DLL jest swobodnie rozpowszechniana jak wiele bibliotek DLL, ale w programie INSTALACYJNYm nadal trzeba zainstalować bibliotekę DLL. Ponadto należy wydać MSVCRTxx.DLL, który zawiera bibliotekę środowiska uruchomieniowego C, która jest używana zarówno przez program, jak i biblioteki DLL MFC.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Jak napisać bibliotekę DLL rozszerzenia MFC

Biblioteka DLL rozszerzenia MFC jest biblioteką DLL zawierającą klasy i funkcje, które umożliwiają wzbogacanie funkcjonalności klas MFC. Biblioteka DLL rozszerzenia MFC używa udostępnionych bibliotek DLL MFC w taki sam sposób jak aplikacja, z kilkoma dodatkowymi zagadnieniami:

- Proces kompilacji jest podobny do kompilowania aplikacji, która korzysta z udostępnionych bibliotek MFC z kilkoma dodatkowymi opcjami kompilatora i konsolidatora.

- Biblioteka DLL rozszerzenia MFC nie ma `CWinApp` klasy pochodnej.

- Biblioteka DLL rozszerzenia MFC musi udostępniać specjalne `DllMain` . AppWizard dostarcza `DllMain` funkcję, którą można modyfikować.

- Biblioteka DLL rozszerzenia MFC zazwyczaj zapewnia procedurę inicjowania, aby utworzyć, `CDynLinkLibrary` Jeśli biblioteka DLL rozszerzenia MFC chce wyeksportować `CRuntimeClass` es lub zasoby do aplikacji. Klasa pochodna `CDynLinkLibrary` może być używana, jeśli dane poszczególnych aplikacji muszą być obsługiwane przez bibliotekę DLL rozszerzenia MFC.

Te zagadnienia opisano szczegółowo poniżej. Należy również zapoznać się z przykładem zaawansowanej koncepcji MFC [DLLHUSK](../overview/visual-cpp-samples.md) , ponieważ ilustruje to:

- Kompilowanie aplikacji przy użyciu bibliotek udostępnionych. (DLLHUSK.EXE jest aplikacją MFC, która łączy dynamicznie z bibliotekami MFC, a także z innymi bibliotekami DLL).

- Kompilowanie biblioteki DLL rozszerzenia MFC. (Należy zwrócić uwagę na flagi specjalne, takie jak te `_AFXEXT` , które są używane podczas tworzenia biblioteki DLL rozszerzenia MFC)

- Dwa przykłady bibliotek DLL rozszerzeń MFC. Jeden wskazuje podstawową strukturę biblioteki DLL rozszerzenia MFC z ograniczonymi eksportami (TESTDLL1), a drugi pokazuje eksportowanie całego interfejsu klasy (TESTDLL2).

Zarówno aplikacja kliencka, jak i wszystkie biblioteki DLL rozszerzenia MFC muszą używać tej samej wersji MFCxx.DLL. Należy postępować zgodnie z Konwencją biblioteki MFC DLL i zapewnić zarówno wersję Debug, jak i wersje detaliczne (/Release) biblioteki DLL rozszerzenia MFC. Dzięki temu programy klienckie mogą kompilować zarówno wersje debugowe, jak i detaliczne aplikacji, a także połączyć je z odpowiednimi wersjami debugowania lub detaliczną wszystkich bibliotek DLL.

> [!NOTE]
> Ze względu na to, że nazwy C++ dekorowanie i Eksportuj, lista eksportu z biblioteki DLL rozszerzenia MFC może różnić się między wersjami Debug i a DLL dla różnych platform. MFCxx.DLL sprzedaży detalicznej zawiera około 2000 punktów wejścia; MFCxxD.DLL debugowania zawiera około 3000 wyeksportowanych punktów wejścia.

### <a name="quick-note-on-memory-management"></a>Szybka Uwaga dotycząca zarządzania pamięcią

Sekcja zatytułowana "Zarządzanie pamięcią" w bliskiej części tej uwagi technicznej zawiera opis implementacji MFCxx.DLL ze współdzieloną wersją MFC. Informacje potrzebne do zaimplementowania pliku DLL rozszerzenia MFC zostały opisane tutaj.

MFCxx.DLL i wszystkie biblioteki DLL rozszerzenia MFC załadowane do przestrzeni adresowej aplikacji klienckiej będą używały tego samego alokatora pamięci, ładowania zasobów i innych stanów MFC "globalna", tak jakby znajdowały się w tej samej aplikacji. Jest to istotne, ponieważ biblioteki DLL inne niż MFC i zwykłe biblioteki MFC DLL, które statycznie łączą się z MFC, są dokładnie takie same i mają każdą bibliotekę DLL, która przydzieli z własnej puli pamięci.

Jeśli biblioteka DLL rozszerzenia MFC przydzieli pamięć, pamięć może swobodnie Intermix z dowolnym innym obiektem przydzielonym przez aplikację. Ponadto, jeśli aplikacja korzystająca z udostępnionych bibliotek MFC ulegnie awarii, ochrona systemu operacyjnego będzie zachować integralność każdej innej aplikacji MFC, która współużytkuje bibliotekę DLL.

Podobnie inne "globalne" Stany MFC, takie jak bieżący plik wykonywalny do ładowania zasobów z, są również udostępniane między aplikacją kliencką i wszystkimi bibliotekami DLL rozszerzenia MFC, a także MFCxx.DLL samej.

### <a name="building-an-mfc-extension-dll"></a>Kompilowanie biblioteki DLL rozszerzenia MFC

Możesz użyć AppWizard, aby utworzyć projekt biblioteki DLL rozszerzenia MFC i automatycznie wygenerował odpowiednie ustawienia kompilatora i konsolidatora. Wygenerował również `DllMain` funkcję, którą można modyfikować.

Jeśli konwertujesz istniejący projekt na bibliotekę DLL rozszerzenia MFC, Zacznij od standardowych reguł tworzenia aplikacji przy użyciu udostępnionej wersji MFC, a następnie wykonaj następujące czynności:

- Dodaj **/D_AFXEXT** do flag kompilatora. W oknie dialogowym właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię preprocesora. Dodaj `_AFXEXT` do pola Zdefiniuj makra oddzielające poszczególne elementy średnikami.

- Usuń przełącznik kompilatora **/Gy** . W oknie dialogowym właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię generowanie kodu. Upewnij się, że opcja "Włącz łączenie na poziomie funkcji" nie jest włączona. Ułatwi to eksportowanie klas, ponieważ konsolidator nie usunie funkcji, do których nie istnieje odwołanie. Jeśli oryginalny projekt jest używany do tworzenia zwykłej biblioteki MFC DLL statycznie połączonej z MFC, należy zmienić opcję kompilatora **/Mt [d]** na **/MD [d]**.

- Utwórz bibliotekę eksportu z opcją **/dll** , aby utworzyć link. Ta wartość zostanie ustawiona podczas tworzenia nowego obiektu docelowego, określając bibliotekę dołączaną dynamicznie Win32 jako typ docelowy.

### <a name="changing-your-header-files"></a>Zmiana plików nagłówkowych

Celem biblioteki DLL rozszerzenia MFC jest zwykle eksportowanie niektórych typowych funkcji do jednej lub wielu aplikacji, które mogą korzystać z tej funkcji. Powoduje to zagotowanie do eksportowania klas i funkcji globalnych, które są dostępne dla aplikacji klienckich.

Aby to zrobić, należy upewnić się, że każda z funkcji Członkowskich jest oznaczona jako zaimportowana lub eksportowana odpowiednio do potrzeb. Wymaga to specjalnych deklaracji: `__declspec(dllexport)` i `__declspec(dllimport)` . Gdy klasy są używane przez aplikacje klienckie, mają być deklarowane jako `__declspec(dllimport)` . Gdy biblioteka DLL rozszerzenia MFC jest tworzona, należy ją zadeklarować jako `__declspec(dllexport)` . Ponadto funkcje muszą zostać rzeczywiście wyeksportowane, dzięki czemu programy klienckie powiążą się z nimi w czasie ładowania.

Aby wyeksportować całą klasę, użyj `AFX_EXT_CLASS` w definicji klasy. To makro jest definiowane przez strukturę, jak `__declspec(dllexport)` w `_AFXDLL` przypadku `_AFXEXT` , gdy jest zdefiniowane, ale zdefiniowane jako `__declspec(dllimport)` when `_AFXEXT` nie jest zdefiniowane. `_AFXEXT`zgodnie z powyższym opisem, jest definiowana tylko podczas kompilowania biblioteki DLL rozszerzenia MFC. Na przykład:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Nie eksportuje całej klasy

Czasami warto wyeksportować tylko jeden z niezbędnych członków klasy. Na przykład, Jeśli eksportujesz `CDialog` klasę pochodną, może być konieczne tylko wyeksportowanie konstruktora i `DoModal` wywołania. Te elementy członkowskie można eksportować za pomocą bibliotek DLL. Plik DEF, ale można go również użyć `AFX_EXT_CLASS` w taki sam sposób, jak w przypadku poszczególnych członków potrzebnych do eksportowania.

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

Po wykonaniu tej czynności może wystąpić problem z dodatkowym problemem, ponieważ nie są już eksportowane wszystkie elementy członkowskie klasy. Problem polega na tym, że makra MFC działają prawidłowo. Niektóre makra pomocnika MFC w rzeczywistości deklarują lub definiują elementy członkowskie danych. W związku z tym te elementy członkowskie danych również muszą zostać wyeksportowane z biblioteki DLL.

Na przykład makro DECLARE_DYNAMIC jest zdefiniowane w następujący sposób podczas kompilowania biblioteki DLL rozszerzenia MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

Linia, która rozpoczyna "static `AFX_DATA` ", deklaruje obiekt statyczny wewnątrz klasy. Aby poprawnie wyeksportować tę klasę i uzyskać dostęp do informacji o środowisku uruchomieniowym z klienta programu. EXE, należy wyeksportować ten obiekt statyczny. Ponieważ obiekt statyczny jest zadeklarowany za pomocą modyfikatora `AFX_DATA` , wystarczy zdefiniować tylko `AFX_DATA` `__declspec(dllexport)` podczas kompilowania biblioteki DLL i zdefiniować go jako `__declspec(dllimport)` podczas kompilowania pliku wykonywalnego klienta.

Jak wspomniano powyżej, `AFX_EXT_CLASS` jest już zdefiniowany w ten sposób. Wystarczy ponownie zdefiniować, `AFX_DATA` aby były takie same jak `AFX_EXT_CLASS` wokół definicji klasy.

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

MFC zawsze używa `AFX_DATA` symbolu na elementach danych, który definiuje w swoich makrach, więc ta technika będzie działała dla wszystkich takich scenariuszy. Na przykład będzie działała DECLARE_MESSAGE_MAP.

> [!NOTE]
> W przypadku eksportowania całej klasy, a nie wybranych elementów członkowskich klasy, statyczne elementy członkowskie danych są automatycznie eksportowane.

Możesz użyć tej samej techniki, aby automatycznie wyeksportować `CArchive` operator wyodrębniania dla klas, które używają makr DECLARE_SERIAL i IMPLEMENT_SERIAL. Wyeksportuj operator archiwum, przeciągając deklaracje klas (znajdujące się w. H plik) z następującym kodem:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Ograniczenia _AFXEXT

Można użyć symbolu wstępnego _**AFXEXT** dla bibliotek DLL rozszerzenia MFC, o ile nie istnieje wiele warstw bibliotek DLL rozszerzeń MFC. Jeśli masz biblioteki DLL rozszerzenia MFC, które wywołują lub pochodzą z klas we własnych bibliotekach DLL rozszerzenia MFC, które następnie pochodzą od klas MFC, należy użyć własnego symbolu preprocesora, aby uniknąć niejednoznaczności.

Problem polega na tym, że w systemie Win32 należy jawnie zadeklarować wszelkie dane tak, jakby zostały `__declspec(dllexport)` wyeksportowane z biblioteki DLL, i `__declspec(dllimport)` Jeśli ma zostać zaimportowany z biblioteki DLL. Podczas definiowania `_AFXEXT` , nagłówki MFC upewnij się, że `AFX_EXT_CLASS` jest prawidłowo zdefiniowany.

Jeśli masz wiele warstw, jeden symbol, taki jak `AFX_EXT_CLASS` nie jest wystarczający, ponieważ biblioteka DLL rozszerzenia MFC może eksportować nowe klasy, a także importować inne klasy z innej biblioteki DLL rozszerzenia MFC. Aby rozwiązać ten problem, należy użyć specjalnego symbolu preprocesora, który wskazuje, że tworzysz bibliotekę DLL w przeciwieństwie do korzystania z biblioteki DLL. Załóżmy na przykład, że istnieją dwie biblioteki DLL rozszerzenia MFC, A.DLL i B.DLL. Każdy z nich eksportuje kilka klas odpowiednio do. H i B. H. B.DLL używa klas z A.DLL. Pliki nagłówkowe będą wyglądać następująco:

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

Po skompilowaniu A.DLL jest skompilowany przy użyciu **/DA_IMPL** i gdy B.DLL jest skompilowana, jest skompilowany z **/DB_IMPL**. Przy użyciu oddzielnych symboli dla każdej biblioteki DLL CExampleB jest eksportowany i CExampleA jest importowana podczas kompilowania B.DLL. CExampleA jest eksportowany podczas kompilowania A.DLL i importowania, gdy jest używany przez B.DLL (lub innego klienta).

Tego typu warstw nie można wykonać podczas korzystania z `AFX_EXT_CLASS` symboli wbudowanych i `_AFXEXT` preprocesora. Opisana powyżej technika pozwala rozwiązać ten problem w sposób, który nie jest w przeciwieństwie do mechanizmu MFC, którego używa, podczas kompilowania bibliotek DLL rozszerzeń MFC, baz danych i sieci.

### <a name="not-exporting-the-entire-class"></a>Nie eksportuje całej klasy

Po ponownym wyeksportowaniu całej klasy należy zachować szczególną ostrożność. Musisz się upewnić, że niezbędne elementy danych utworzone przez makra MFC są poprawnie wyeksportowane. Można to zrobić przez ponowne zdefiniowanie `AFX_DATA` do określonego makra klasy. Należy to zrobić za każdym razem, gdy nie eksportujesz całej klasy.

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

Poniżej znajduje się dokładny kod, który należy umieścić w głównym pliku źródłowym dla biblioteki DLL rozszerzenia MFC. Powinien on występować po standardowym uwzględnieniu. Należy pamiętać, że w przypadku korzystania z programu AppWizard do tworzenia plików początkowych dla biblioteki DLL rozszerzenia MFC dostarcza `DllMain` dla Ciebie.

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

Wywołanie `AfxInitExtensionModule` przechwytuje moduły uruchomieniowe modułów ( `CRuntimeClass` struktury), a także jego fabryki obiektów `COleObjectFactory` do użycia w przyszłości podczas `CDynLinkLibrary` tworzenia obiektu. Wywołanie (opcjonalne) `AfxTermExtensionModule` umożliwia MFC Oczyszczanie biblioteki DLL rozszerzenia MFC, gdy każdy proces zostanie odłączony (co dzieje się po zakończeniu procesu lub gdy biblioteka DLL zostaje zwolniona w wyniku `FreeLibrary` wywołania) z biblioteki DLL rozszerzenia MFC. Ponieważ większość bibliotek DLL rozszerzeń MFC nie są ładowane dynamicznie (zazwyczaj są one połączone za pośrednictwem ich bibliotek importu), wywołanie `AfxTermExtensionModule` jest zwykle niepotrzebne.

Jeśli aplikacja ładuje i zwalnia biblioteki DLL rozszerzenia MFC dynamicznie, należy wywołać `AfxTermExtensionModule` jak pokazano powyżej. Upewnij się również, że funkcja `AfxLoadLibrary` and `AfxFreeLibrary` (zamiast Functions `LoadLibrary` i `FreeLibrary` ) używa wielu wątków lub dynamicznie ładuje bibliotekę MFC DLL. Za pomocą `AfxLoadLibrary` i `AfxFreeLibrary` upewnij się, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest załadowana i zwolniona, nie powoduje uszkodzenia globalnego stanu MFC.

Plik nagłówka AFXDLLX. H zawiera specjalne definicje struktur używanych w bibliotekach DLL rozszerzenia MFC, takich jak definicja dla `AFX_EXTENSION_MODULE` i `CDynLinkLibrary` .

Globalna *extensionDLL* musi być zadeklarowana jako pokazana. W przeciwieństwie do 16-bitowej wersji MFC, można przydzielić pamięć i wywoływać funkcje MFC w tym czasie, ponieważ MFCxx.DLL jest w pełni inicjowane przez czas `DllMain` wywoływany przez użytkownika.

### <a name="sharing-resources-and-classes"></a>Udostępnianie zasobów i klas

Proste biblioteki DLL rozszerzeń MFC potrzebują tylko wyeksportować kilka funkcji o niskiej przepustowości do aplikacji klienckiej i nic nie rób. Więcej bibliotek DLL intensywnie korzystających z interfejsu użytkownika może chcieć wyeksportować zasoby i klasy języka C++ do aplikacji klienckiej.

Eksportowanie zasobów odbywa się za pomocą listy zasobów. W każdej aplikacji jest pojedynczo dołączoną listą `CDynLinkLibrary` obiektów. Podczas wyszukiwania zasobu większość standardowych implementacji MFC, które ładują zasoby, najpierw sprawdzają się w bieżącym module zasobów ( `AfxGetResourceHandle` ) i jeśli nie została znaleziona, przeprowadzi listę `CDynLinkLibrary` obiektów próbujących załadować żądany zasób.

Dynamiczne tworzenie obiektów języka C++ z nazwą klasy języka C++ jest podobne. Mechanizm deserializacji obiektu MFC musi mieć wszystkie `CRuntimeClass` zarejestrowane obiekty, aby można je było odtworzyć przez dynamiczne utworzenie obiektu C++ dla wymaganego typu w oparciu o to, co zostało wcześniej zapisane.

Jeśli aplikacja kliencka ma używać klas w bibliotece DLL rozszerzenia MFC, które są `DECLARE_SERIAL` , należy wyeksportować klasy, aby były widoczne dla aplikacji klienckiej. Jest to również wykonywane przez przechodzenie do `CDynLinkLibrary` listy.

W przypadku przykładowej zaawansowanej koncepcji MFC [DLLHUSK](../overview/visual-cpp-samples.md), lista wygląda następująco:

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

MFCxx.DLL zazwyczaj znajduje się na liście zasobów i klas. MFCxx.DLL obejmuje wszystkie standardowe zasoby MFC, w tym ciągi monitów dla wszystkich identyfikatorów poleceń standardowych. Umieszczenie go na końcu listy umożliwia Bibliotekom DLL i aplikacji klienckiej nie posiadanie własnej kopii standardowych zasobów MFC, ale w zamian polega na zasobach udostępnionych w MFCxx.DLL.

Scalanie zasobów i nazw klas wszystkich bibliotek DLL w przestrzeni nazw aplikacji klienta ma wady, które należy zachować ostrożność podczas wybierania identyfikatorów lub nazw. Można wyłączyć tę funkcję, nie eksportując zasobów lub `CDynLinkLibrary` obiektów do aplikacji klienckiej. Przykład [DLLHUSK](../overview/visual-cpp-samples.md) służy do zarządzania współużytkowaną przestrzenią nazw zasobów przy użyciu wielu plików nagłówkowych. Zobacz [Uwagi techniczne 35](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) , aby uzyskać porady dotyczące korzystania z plików zasobów udostępnionych.

### <a name="initializing-the-dll"></a>Inicjowanie biblioteki DLL

Jak wspomniano powyżej, zazwyczaj należy utworzyć `CDynLinkLibrary` obiekt w celu wyeksportowania zasobów i klas do aplikacji klienckiej. Musisz podać wyeksportowany punkt wejścia, aby zainicjować bibliotekę DLL. Co więcej, jest to procedura void, która nie przyjmuje argumentów i zwraca wartość Nothing, ale może być dowolna.

Wszystkie aplikacje klienckie, które chcą korzystać z biblioteki DLL, muszą wywołać tę procedurę inicjowania, jeśli używasz tego podejścia. Możesz również przydzielić ten `CDynLinkLibrary` obiekt `DllMain` bezpośrednio po wywołaniu `AfxInitExtensionModule` .

Procedura inicjowania musi utworzyć `CDynLinkLibrary` obiekt w stercie bieżącej aplikacji, który jest połączony z informacjami o bibliotece DLL rozszerzenia MFC. Można to zrobić przy użyciu następujących czynności:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Nazwa procedury, *InitXxxDLL* w tym przykładzie, może być dowolna. Nie musi to być **extern "C"**, ale dzięki temu łatwiejsze jest zachowanie listy eksportu.

> [!NOTE]
> Jeśli biblioteka DLL rozszerzenia MFC jest używana ze zwykłej biblioteki MFC DLL, należy wyeksportować tę funkcję inicjującą. Ta funkcja musi zostać wywołana ze zwykłej biblioteki MFC DLL przed użyciem klas lub zasobów biblioteki DLL rozszerzenia MFC.

### <a name="exporting-entries"></a>Eksportowanie wpisów

Prostym sposobem eksportowania klas jest użycie `__declspec(dllimport)` i `__declspec(dllexport)` dla każdej klasy i funkcji globalnej, która ma zostać wyeksportowana. Znacznie ułatwia to, ale jest mniej wydajne niż nazewnictwo każdego punktu wejścia (opisanego poniżej), ponieważ ma mniej kontroli nad tym, jakie funkcje są eksportowane i nie można eksportować funkcji według liczby porządkowej. TESTDLL1 i TESTDLL2 używają tej metody do eksportowania swoich wpisów.

Bardziej wydajna Metoda (i Metoda używana przez MFCxx.DLL) polega na wyeksportowaniu każdego wpisu w odróżnieniu od nazw poszczególnych wpisów w. Plik DEF. Ze względu na to, że eksportuje się selektywne eksporty z naszej biblioteki DLL (to nie wszystko), należy zdecydować, które z określonych interfejsów chcemy wyeksportować. Jest to trudne, ponieważ należy określić nazwy zniekształcona dla konsolidatora w postaci wpisów w. Plik DEF. Nie należy eksportować żadnych klas języka C++, chyba że naprawdę konieczne jest posiadanie symbolicznego linku.

Jeśli podjęto próbę eksportowania klas C++ za pomocą. Plik DEF przed, warto utworzyć narzędzie do automatycznego wygenerowania tej listy. Można to zrobić przy użyciu dwuetapowego procesu linku. Połącz bibliotekę DLL raz z brakiem eksportu i zezwól konsolidatorowi na wygenerowanie elementu. Plik mapy. Polu. Za pomocą pliku mapy można wygenerować listę funkcji, które mają zostać wyeksportowane, dzięki czemu może być używana do generowania wpisów eksportu dla. Plik DEF. Lista eksportu dla MFCxx.DLL i biblioteki DLL rozszerzeń MFC OLE i bazy danych (liczba tysięcy) została wygenerowana przy użyciu takiego procesu (mimo że nie jest ona całkowicie automatyczna i wymaga dostrojenia co jakiś czas).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp a CDynLinkLibrary

Biblioteka DLL rozszerzenia MFC nie ma `CWinApp` obiektu pochodnego; zamiast tego musi współdziałać z `CWinApp` obiektem pochodnym aplikacji klienckiej. Oznacza to, że aplikacja kliencka jest właścicielem głównej pompy komunikatów, pętli bezczynności i tak dalej.

Jeśli biblioteka DLL rozszerzenia MFC musi obsługiwać dodatkowe dane dla każdej aplikacji, można utworzyć nową klasę z `CDynLinkLibrary` i stworzyć ją w InitXxxDLL procedurę opisany powyżej. Podczas uruchamiania Biblioteka DLL może sprawdzić listę obiektów bieżącej aplikacji, `CDynLinkLibrary` Aby znaleźć tę, dla której dana Biblioteka DLL rozszerzenia MFC.

### <a name="using-resources-in-your-dll-implementation"></a>Używanie zasobów w implementacji biblioteki DLL

Jak wspomniano powyżej, domyślne obciążenie zasobów przeprowadzi listę `CDynLinkLibrary` obiektów szukających pierwszego pliku exe lub dll, który ma żądany zasób. Wszystkie interfejsy API MFC oraz cały kod wewnętrzny używa `AfxFindResourceHandle` do przeszukiwania listy zasobów w celu znalezienia dowolnego zasobu, niezależnie od miejsca, w którym może się znajdować.

Jeśli chcesz ładować tylko zasoby z określonego miejsca, Użyj interfejsów API `AfxGetResourceHandle` i `AfxSetResourceHandle` Zapisz stary uchwyt i Ustaw nowe dojście. Należy pamiętać o przywróceniu starego uchwytu zasobów przed zwróceniem do aplikacji klienckiej. Przykładowa TESTDLL2 używa tego podejścia do jawnego ładowania menu.

Przechodzenie listy ma wady, które są nieco wolniejsze i wymaga zarządzania zakresami identyfikatorów zasobów. Ma ona zalety, aby aplikacja kliencka, która łączy się z kilkoma bibliotekami DLL rozszerzenia MFC, mogła używać dowolnego zasobu dostarczonego z biblioteką DLL bez konieczności określania dojścia do wystąpienia biblioteki DLL. `AfxFindResourceHandle`jest interfejsem API służącym do przechodzenia do listy zasobów w celu wyszukania danego dopasowania. Przyjmuje nazwę i typ zasobu i zwraca dojście do zasobu, w którym została najpierw znaleziona (lub ma wartość NULL).

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Pisanie aplikacji korzystającej z wersji biblioteki DLL

### <a name="application-requirements"></a>Wymagania dotyczące aplikacji

Aplikacja, która używa udostępnionej wersji MFC, musi być zgodna z kilkoma prostymi regułami:

- Musi mieć `CWinApp` obiekt i przestrzegać standardowych reguł dla pompy komunikatów.

- Musi być skompilowany z zestawem wymaganych flag kompilatora (patrz poniżej).

- Musi on łączyć się z bibliotekami importu MFCxx. Ustawiając wymagane flagi kompilatora, nagłówki MFC są określane w czasie łącza, z którym biblioteka powinna łączyć się aplikacja.

- Aby uruchomić plik wykonywalny, MFCxx.DLL musi znajdować się na ścieżce lub w katalogu systemu Windows.

### <a name="building-with-the-development-environment"></a>Kompilowanie za pomocą środowiska programistycznego

Jeśli używasz wewnętrznego pliku reguł programu make z większością standardowych ustawień domyślnych, możesz łatwo zmienić projekt, aby skompilować wersję biblioteki DLL.

W poniższym kroku założono, że masz prawidłowo działającą aplikację MFC połączoną z NAFXCWD. LIB (na potrzeby debugowania) i NAFXCW. LIB (dla sprzedaży detalicznej) i chcesz ją przekonwertować, aby użyć udostępnionej wersji biblioteki MFC. Korzystasz ze środowiska Visual C++ i masz wewnętrzny plik projektu.

1. W menu **projekty** kliknij polecenie **Właściwości**. Na stronie **Ogólne** w obszarze **Ustawienia domyślne projektu**Ustaw Microsoft Foundation Classes na **Używanie MFC w współdzielonej bibliotece DLL** (MFCxx (d). dll).

### <a name="building-with-nmake"></a>Kompilowanie za pomocą NMAKE

Jeśli używasz funkcji zewnętrznego pliku reguł programu make Visual C++ lub używasz programu NMAKE bezpośrednio, musisz edytować swój plik reguł programu make, aby obsługiwał opcje kompilatora i konsolidatora

Wymagane flagi kompilatora:

- **/D_AFXDLL/MD** 
   **/D_AFXDLL**

Standardowe nagłówki MFC muszą mieć ten symbol do zdefiniowania:

- **/MD** Aplikacja musi używać wersji biblioteki DLL biblioteki wykonawczej C

Wszystkie inne flagi kompilatora stosują się do domyślnych ustawień MFC (na przykład _DEBUG do debugowania).

Edytuj listę konsolidatora bibliotek. Zmień NAFXCWD. LIB do MFCxxD. LIB i zmiana NAFXCW. LIB do MFCxx. LIB. Zastąp LIBC. LIB z MSVCRT. LIB. Podobnie jak w przypadku każdej innej biblioteki MFC, ważne jest, aby MFCxxD. LIB został umieszczony **przed** wszystkimi bibliotekami środowiska uruchomieniowego C.

Opcjonalnie Dodaj **/D_AFXDLL** do opcji kompilatora zasobów dla handlu detalicznego i debugowania (ten, który faktycznie kompiluje zasoby z **/r**). Powoduje to, że końcowy plik wykonywalny jest mniejszy przez udostępnienie zasobów znajdujących się w bibliotekach DLL MFC.

Po wprowadzeniu tych zmian wymagana jest pełna ponowna kompilacja.

### <a name="building-the-samples"></a>Kompilowanie przykładów

Większość przykładowych programów MFC można skompilować z Visual C++ lub z udostępnionego pliku reguł programu make zgodnego z NMAKE z wiersza polecenia.

Aby przekonwertować dowolny z tych przykładów do użycia MFCxx.DLL, można załadować. Plik MAK do Visual C++ i ustaw opcje projektu zgodnie z powyższym opisem. W przypadku korzystania z kompilacji NMAKE można określić wartość "AFXDLL = 1" w wierszu polecenia NMAKE, która spowoduje skompilowanie przykładu przy użyciu udostępnionych bibliotek MFC.

Przykład [DLLHUSK](../overview/visual-cpp-samples.md) zaawansowanych koncepcji MFC jest kompilowany z biblioteką DLL MFC. Ten przykład nie tylko ilustruje sposób kompilowania aplikacji połączonej z MFCxx.DLL, ale również przedstawia inne funkcje opcji pakietów DLL MFC, takich jak biblioteki DLL rozszerzenia MFC opisane w dalszej części tej uwagi technicznej.

### <a name="packaging-notes"></a>Informacje o pakowaniu

Wersja handlowa bibliotek DLL (MFCxx [U]. DLL) są swobodnie redystrybucyjne. Wersja do debugowania bibliotek DLL nie jest swobodnie rozpowszechniana i powinna być używana tylko podczas opracowywania aplikacji.

Biblioteki DLL debugowania są udostępniane z informacjami o debugowaniu. Za pomocą debugera Visual C++ można śledzić wykonywanie aplikacji oraz biblioteki DLL. Wersje DLL (MFCxx [U]). DLL) nie zawiera informacji o debugowaniu.

W przypadku dostosowywania lub ponownego kompilowania bibliotek DLL, należy wywołać je coś innego niż "MFCxx" w pliku MFC SRC MFCDLL. Klucz MAK zawiera opis opcji kompilacji i zawiera logikę zmiany nazwy biblioteki DLL. Zmiana nazwy plików jest konieczna, ponieważ te biblioteki DLL mogą być współużytkowane przez wiele aplikacji MFC. Jeśli niestandardowa wersja bibliotek DLL MFC zastąpią zainstalowane w systemie, można przerwać inną aplikację MFC przy użyciu udostępnionych bibliotek DLL MFC.

Nie zaleca się ponownego kompilowania bibliotek DLL MFC.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Sposób implementacji MFCxx.DLL

W poniższej sekcji opisano sposób implementacji biblioteki MFC DLL (MFCxx.DLL i MFCxxD.DLL). Informacje szczegółowe są również nieważne, jeśli wszystko, co chcesz zrobić, jest używane przez bibliotekę MFC DLL z aplikacją. Szczegóły w tym miejscu nie są niezbędne do poznania sposobu pisania biblioteki DLL rozszerzenia MFC, ale zrozumienie tej implementacji może pomóc w pisaniu własnej biblioteki DLL.

### <a name="implementation-overview"></a>Przegląd implementacji

Biblioteka MFC DLL jest naprawdę specjalnym przypadkiem biblioteki DLL rozszerzenia MFC, jak opisano powyżej. Ma bardzo dużą liczbę eksportów dla dużej liczby klas. Istnieje kilka dodatkowych czynności w bibliotece MFC DLL, które sprawiają, że jest ona jeszcze bardziej specjalna niż zwykła Biblioteka DLL rozszerzenia MFC.

### <a name="win32-does-most-of-the-work"></a>Win32 wykonuje większość pracy

16-bitowa wersja MFC wymagała szeregu specjalnych technik, w tym danych dla poszczególnych aplikacji w segmencie stosu, specjalnych segmentów utworzonych przez część kodu zestawu 80x86, kontekstów wyjątków dla procesów i innych technik. System Win32 bezpośrednio obsługuje dane poszczególnych procesów w bibliotece DLL, co jest potrzebne w większości czasu. W przypadku większości MFCxx.DLL jest tylko NAFXCW. Biblioteka LIB spakowana w bibliotece DLL. Jeśli szukasz kodu źródłowego MFC, znajdziesz kilka #ifdef _AFXDLL, ponieważ istnieją bardzo specjalne przypadki, które należy wykonać. Specjalne przypadki, w których istnieją szczególne problemy dotyczące środowiska Win32 w systemie Windows 3,1 (nazywanego również Win32s). Win32s nie obsługuje danych bibliotek DLL dla poszczególnych procesów bezpośrednio, dlatego Biblioteka MFC DLL musi używać interfejsów API Win32 do uzyskiwania danych lokalnych.

### <a name="impact-on-library-sources-additional-files"></a>Wpływ na źródła biblioteki, dodatkowe pliki

Wpływ wersji **_AFXDLL** na normalne źródła biblioteki klas MFC i nagłówki jest stosunkowo drobny. Istnieje specjalny plik wersji (AFXV_DLL. H) oraz dodatkowy plik nagłówka (AFXDLL_. H) zawartej w głównym AFXWIN. Nagłówek H. AFXDLL_. Nagłówek H zawiera `CDynLinkLibrary` klasę i inne szczegóły implementacji zarówno `_AFXDLL` aplikacji, jak i bibliotek DLL rozszerzeń MFC. AFXDLLX. Nagłówek H jest dostarczany do kompilowania bibliotek DLL rozszerzeń MFC (patrz powyżej, aby uzyskać szczegółowe informacje).

Regularne źródła do biblioteki MFC w bibliotece MFC SRC mają dodatkowy kod warunkowy pod `_AFXDLL` #ifdef. Dodatkowy plik źródłowy (DLLINIT. CPP) zawiera dodatkowy kod inicjalizacji biblioteki DLL i inne kleje dla udostępnionej wersji biblioteki MFC.

W celu skompilowania udostępnionej wersji MFC są udostępniane dodatkowe pliki. (Zobacz poniżej, aby uzyskać szczegółowe informacje na temat sposobu kompilowania biblioteki DLL).

- Tymi. Pliki DEF są używane do eksportowania punktów wejścia biblioteki MFC DLL do wersji Debug (MFCxxD. DEF) i Release (MFCxx. DEF) biblioteki DLL.

- Wskazani. Plik RC (MFCDLL. RC) zawiera wszystkie standardowe zasoby MFC i zasób VERSIONINFO dla biblioteki DLL.

- Z. Plik CLW (MFCDLL. CLW) umożliwia przeglądanie klas MFC przy użyciu ClassWizard. Uwaga: Ta funkcja nie jest określona w odróżnieniu od wersji biblioteki DLL MFC.

### <a name="memory-management"></a>Zarządzanie pamięcią

Aplikacja używająca MFCxx.DLL korzysta ze wspólnego alokatora pamięci dostarczonego przez MSVCRTxx.DLL, współużytkowanej biblioteki DLL środowiska uruchomieniowego C. Aplikacja, wszystkie biblioteki DLL rozszerzenia MFC, a także biblioteki MFC DLL same używają tego alokatora pamięci współdzielonej. Za pomocą udostępnionego pliku DLL do alokacji pamięci biblioteki MFC mogą przydzielić pamięć, która jest później zwalniana przez aplikację lub odwrotnie. Ponieważ zarówno aplikacja, jak i Biblioteka DLL muszą używać tego samego alokatora, nie należy przesłaniać globalnego **operatora C++ New** ani **operator delete**. Te same reguły dotyczą pozostałej części procedur alokacji pamięci w czasie wykonywania C (takich jak **malloc**, zmiana **alokacji**, **bezpłatna**i inne).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Liczby porządkowe i klasy __declspec (dllexport) i nazwy bibliotek DLL

Nie używamy `class` **`__declspec(dllexport)`** funkcjonalności kompilatora języka C++. Zamiast tego lista eksportów jest dołączona do źródeł biblioteki klas (MFCxx. DEF i MFCxxD. DEF). Eksportowane są tylko te wybrane punkty wejścia (funkcje i dane). Inne symbole, takie jak funkcje lub klasy prywatnej implementacji MFC, nie są eksportowane wszystkie operacje eksportu są wykonywane przez numer porządkowy bez nazwy ciągu w tabeli nazw rezydentnych lub nierezydentnych.

Korzystanie z programu `class` **`__declspec(dllexport)`** może być efektywną alternatywą dla tworzenia mniejszych bibliotek DLL, ale w przypadku dużej biblioteki DLL, takiej jak MFC, domyślny mechanizm eksportowania ma limity wydajności i pojemności.

Oznacza to, że firma Microsoft może spakować wiele funkcji w MFCxx.DLL wersji, która jest około 800 KB bez kompromisu w zakresie wykonywania lub szybkości ładowania. MFCxx.DLL byłoby 100 000 większe, ale ta technika nie została użyta. Umożliwia to również dodanie dodatkowych punktów wejścia na końcu. Plik DEF, który umożliwia proste przechowywanie wersji bez wpływu na szybkość i wydajność eksportowania według liczby porządkowej. Wersje główne wersji biblioteki klas MFC zmienią nazwę biblioteki. Oznacza to, że MFC30.DLL to biblioteka DLL redystrybucyjna zawierająca wersję 3,0 biblioteki klas MFC. Uaktualnienie tej biblioteki DLL, powiedzmy, w hipotetycznej MFC 3,1, biblioteka DLL powinna mieć nazwę MFC31.DLL. Ponownie, jeśli zmodyfikujesz kod źródłowy MFC w celu utworzenia niestandardowej wersji biblioteki MFC DLL, użyj innej nazwy (i najlepiej bez "MFC" w nazwie).

## <a name="see-also"></a>Zobacz także

[Uwagi techniczne według numeru](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
