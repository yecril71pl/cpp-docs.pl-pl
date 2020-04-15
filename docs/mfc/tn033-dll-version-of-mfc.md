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
ms.openlocfilehash: ad4cb883cfe7e397cf599d659afb02b23501dc5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370314"
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: wersja DLL biblioteki MFC

W tej notatce opisano, jak można używać bibliotek łączeń MCxx.DLL i MFCxxD.DLL (gdzie x jest numerem wersji MFC) udostępnionych bibliotek łączy dynamicznych z aplikacjami MFC i bibliotekami DLL rozszerzenia MFC. Aby uzyskać więcej informacji na temat zwykłych bibliotek DLL MFC, zobacz [Korzystanie z MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

Niniejsza uwaga techniczna obejmuje trzy aspekty bibliotek DLL. Dwa ostatnie są dla bardziej zaawansowanych użytkowników:

- [Jak utworzyć bibliotekę DLL rozszerzenia MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)

- [Jak utworzyć aplikację MFC, która używa wersji DLL MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)

- [Jak implementowane są udostępnione biblioteki łączy dynamicznych MFC](#_mfcnotes_how_the_mfc30.dll_is_implemented)

Jeśli jesteś zainteresowany tworzeniem biblioteki DLL przy użyciu MFC, która może być używana z aplikacjami innych niż MFC (jest to nazywane zwykłą biblioteką DLL MFC), zapoznaj się [z notą techniczną 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md).

## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Omówienie obsługi mfcxx.DLL: Terminologia i pliki

**Regularne biblioteki DLL MFC:** Używasz zwykłej biblioteki DLL MFC do tworzenia autonomicznej biblioteki DLL przy użyciu niektórych klas MFC. Interfejsy w granicach App/DLL są interfejsami "C", a aplikacja kliencka nie musi być aplikacją MFC.

Jest to wersja obsługi biblioteki DLL obsługiwane w MFC 1.0. Jest on opisany w [technical note 11](../mfc/tn011-using-mfc-as-part-of-a-dll.md) i MFC Advanced Concepts próbki [DLLScreenCap](../overview/visual-cpp-samples.md).

> [!NOTE]
> Od wersji Visual C++ 4.0 termin **USRDLL** jest przestarzały i został zastąpiony przez zwykłą bibliotekę DLL MFC, która statycznie łączy się z MFC. Można również utworzyć regularne MFC DLL, który dynamicznie łączy się z MFC.

MFC 3.0 (i powyżej) obsługuje regularne biblioteki DLL MFC ze wszystkimi nowymi funkcjami, w tym ole i klas bazy danych.

**AFXDLL:** Jest to również określane jako udostępniona wersja bibliotek MFC. Jest to nowa obsługa biblioteki DLL dodana w MFC 2.0. Sama biblioteka MFC znajduje się w wielu bibliotekach DLL (opisanych poniżej), a aplikacja kliencka lub biblioteka DLL dynamicznie łączy wymagane biblioteki DLL. Interfejsy w całej granicy aplikacji/biblioteki DLL są interfejsy klasy C++/MFC. Aplikacja kliencka MUSI być aplikacją MFC. Obsługuje wszystkie funkcje MFC 3.0 (wyjątek: UNICODE nie jest obsługiwany dla klas bazy danych).

> [!NOTE]
> Od wersji 4.0 visual C++ ten typ biblioteki DLL jest określany jako "DLL rozszerzenia".

W tej notatce będzie używana biblioteka MFCxx.DLL w celu odnośnia się od całego zestawu bibliotek dll MFC, który zawiera:

- Debugowanie: MFCxxD.DLL (połączone) i MFCSxxD.LIB (statyczne).

- Wydanie: MFCxx.DLL (połączone) i MFCSxx.LIB (statyczne).

- Debugowanie Unicode: MFCxxUD.DLL (połączone) i MFCSxxD.LIB (statyczne).

- Wydanie Unicode: MFCxxU.DLL (połączone) i MFCSxxU.LIB (statyczne).

> [!NOTE]
> The MFCSxx[U][D]. Biblioteki LIB są używane w połączeniu z bibliotekami bibliotek DLL udostępnionych MFC. Te biblioteki zawierają kod, który musi być statycznie połączony z aplikacją lub biblioteką DLL.

Aplikacja łączy się z odpowiednimi bibliotekami importu:

- Debugowanie: MFCxxD.LIB

- Wydanie: MFCxx.LIB

- Debugowanie Unicode: MFCxxUD.LIB

- Wydanie Unicode: MFCxxU.LIB

"Biblioteka DLL rozszerzenia MFC" jest biblioteką DLL opartą na pliku MFCxx.DLL (i/lub innych udostępnionych bibliotek DLL MFC). Tutaj rozpoczyna się architektura składnika MFC. Jeśli pochodzisz przydatne klasy z klasy MFC lub utworzyć inny zestaw narzędzi mfc, można umieścić go w DLL. Ta biblioteka DLL używa mfcxx.DLL, podobnie jak ostateczna aplikacja kliencka. Umożliwia to wielokrotnego używalnia klas liści, klas podstawowych wielokrotnegoużytnia i klas widoku/dokumentu wielokrotnegoużytnia.

## <a name="pros-and-cons"></a>Plusy i minusy

Dlaczego warto korzystać ze udostępnionej wersji MFC

- Korzystanie z biblioteki udostępnionej może spowodować mniejsze aplikacje (minimalna aplikacja, która używa większości biblioteki MFC jest mniejsza niż 10K).

- Udostępniona wersja MFC obsługuje biblioteki DLL rozszerzenia MFC i zwykłe biblioteki DLL MFC.

- Tworzenie aplikacji, która używa udostępnionych bibliotek MFC jest szybsze niż tworzenie statycznie połączone aplikacji MFC, ponieważ nie jest konieczne łączenie MFC się. Jest to szczególnie prawdziwe w **debug** kompilacji, gdzie konsolidator musi kompaktować informacje debugowania — łącząc się z biblioteką DLL, która już zawiera informacje debugowania, jest mniej informacji debugowania do kompaktowania w aplikacji.

Dlaczego nie należy używać udostępnionej wersji MFC:

- Wysyłka aplikacji korzystającej z biblioteki udostępnionej wymaga wysłania biblioteki MFCxx.DLL (i innych) z programem. MFCxx.DLL jest swobodnie redystrybucyjny jak wiele bibliotek DLL, ale nadal należy zainstalować bibliotekę DLL w programie SETUP. Ponadto należy wysłać bibliotekę MSVCRTxx.DLL, która zawiera bibliotekę środowiska wykonawczego C, która jest używana zarówno przez program, jak i przez same biblioteki DLL MFC.

## <a name="how-to-write-an-mfc-extension-dll"></a><a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Jak napisać bibliotekę DLL rozszerzenia MFC

Biblioteka DLL rozszerzenia MFC jest biblioteką DLL zawierającą klasy i funkcje napisane w celu upiększania funkcjonalności klas MFC. Biblioteka DLL rozszerzenia MFC używa udostępnionych bibliotek DLL MFC w taki sam sposób, w jaki aplikacja używa go, z kilkoma dodatkowymi zagadnieniami:

- Proces kompilacji jest podobny do tworzenia aplikacji, która używa udostępnionych bibliotek MFC z kilkoma dodatkowymi opcjami kompilatora i konsolidatora.

- Biblioteka DLL rozszerzenia MFC `CWinApp`nie ma klasy pochodnej.

- Biblioteka DLL rozszerzenia MFC `DllMain`musi zawierać specjalny plik . AppWizard dostarcza `DllMain` funkcję, którą można modyfikować.

- Biblioteka DLL rozszerzenia MFC zwykle zapewnia procedurę `CDynLinkLibrary` inicjowania, aby utworzyć, `CRuntimeClass`jeśli biblioteka DLL rozszerzenia MFC chce wyeksportować es lub zasobów do aplikacji. Klasa pochodna `CDynLinkLibrary` może być używana, jeśli dane dla aplikacji muszą być przechowywane przez bibliotekę DLL rozszerzenia MFC.

Zagadnienia te są opisane bardziej szczegółowo poniżej. Należy również odwołać się do przykładu MFC Advanced Concepts [DLLHUSK,](../overview/visual-cpp-samples.md) ponieważ ilustruje:

- Tworzenie aplikacji przy użyciu bibliotek udostępnionych. (DLLHUSK. EXE to aplikacja MFC, która dynamicznie łączy się z bibliotekami MFC, a także z innymi bibliotekami DLL.)

- Tworzenie biblioteki DLL rozszerzenia MFC. (Zwróć uwagę na `_AFXEXT` specjalne flagi, takie jak te są używane w budowaniu DLL rozszerzenie MFC)

- Dwa przykłady bibliotek DLL rozszerzenia MFC. Jeden pokazuje podstawową strukturę biblioteki DLL rozszerzenia MFC z ograniczonym eksportem (TESTDLL1), a drugi pokazuje eksportowanie interfejsu całej klasy (TESTDLL2).

Zarówno aplikacja kliencka, jak i wszelkie biblioteki DLL rozszerzenia MFC muszą używać tej samej wersji biblioteki MFCxx.DLL. Należy postępować zgodnie z konwencją biblioteki DLL MFC i zapewnić zarówno debugowania i detalicznej (wydanie) wersja biblioteki DLL rozszerzenia MFC. Pozwala to programom klienckim na tworzenie zarówno debugowania, jak i wersji detalicznych swoich aplikacji i łączenie ich z odpowiednią wersją debugowania lub detalicznej wszystkich bibliotek DLL.

> [!NOTE]
> Ponieważ c++ nazwa mangling i eksportu problemów, lista eksportu z biblioteki DLL rozszerzenia MFC może być inna między debugowania i wersji detalicznych tej samej biblioteki DLL i bibliotek DLL dla różnych platform. Detaliczna MFCxx.DLL ma około 2000 eksportowanych punktów wejścia; debugowania MFCxxD.DLL ma około 3000 eksportowanych punktów wejścia.

### <a name="quick-note-on-memory-management"></a>Krótka uwaga dotycząca zarządzania pamięcią

Sekcja zatytułowana "Zarządzanie pamięcią", na końcu tej uwagi technicznej, opisuje implementację mfcxx.DLL z udostępnionej wersji MFC. Informacje, które musisz wiedzieć, aby zaimplementować tylko bibliotekę DLL rozszerzenia MFC jest opisany tutaj.

MFCxx.DLL i wszystkie biblioteki DLL rozszerzenia MFC załadowane do przestrzeni adresowej aplikacji klienckiej będą używać tego samego alokatora pamięci, ładowania zasobów i innych stanów "globalnych" MFC, tak jakby znajdowały się w tej samej aplikacji. Jest to istotne, ponieważ biblioteki DLL innych niż MFC i regularne biblioteki DLL MFC, które statycznie łączą się z MFC zrobić dokładnie odwrotnie i mają każdą bibliotekę DLL przydzielanie z własnej puli pamięci.

Jeśli biblioteka DLL rozszerzenia MFC przydziela pamięć, a następnie tej pamięci można swobodnie mieszać z dowolnego innego obiektu przydzielonego aplikacji. Ponadto jeśli aplikacja, która używa udostępnionych bibliotek MFC ulegnie awarii, ochrona systemu operacyjnego zachowa integralność innych aplikacji MFC współużytkuje biblioteki DLL.

Podobnie inne "globalne" stany MFC, takie jak bieżący plik wykonywalny do ładowania zasobów, są również współużytkowane między aplikacją kliencką i wszystkimi bibliotekami DLL rozszerzenia MFC, a także samą biblioteką MFCxx.DLL.

### <a name="building-an-mfc-extension-dll"></a>Tworzenie biblioteki DLL rozszerzenia MFC

Za pomocą AppWizard można utworzyć projekt DLL rozszerzenia MFC i automatycznie wygeneruje odpowiednie ustawienia kompilatora i konsolidatora. Był również wygenerować `DllMain` funkcję, którą można modyfikować.

Jeśli konwertujesz istniejący projekt na bibliotekę DLL rozszerzenia MFC, zacznij od standardowych reguł tworzenia aplikacji przy użyciu udostępnionej wersji MFC, a następnie wykonaj następujące czynności:

- Dodaj **/D_AFXEXT** do flag kompilatora. W oknie dialogowym Właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię Preprocesora. Dodaj `_AFXEXT` do pola Definiuj makra, oddzielając każdy z elementów średnikami.

- Usuń przełącznik kompilatora **/Gy.** W oknie dialogowym Właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię Generowanie kodu. Upewnij się, że opcja "Włącz łączenie na poziomie funkcji" nie jest włączona. Ułatwi to eksportowanie klas, ponieważ konsolidator nie usunie funkcji bez odwołań. Jeśli oryginalny projekt jest używany do tworzenia regularnych MFC DLL statycznie połączone z MFC, zmień **/MT[d]** opcja kompilatora **/MD[d]**.

- Tworzenie biblioteki eksportu z **/DLL** opcji LINK. Zostanie to ustawione podczas tworzenia nowego obiektu docelowego, określając bibliotekę dynamicznego łącza Win32 jako typ docelowy.

### <a name="changing-your-header-files"></a>Zmienianie plików nagłówkowych

Celem biblioteki DLL rozszerzenia MFC jest zwykle eksportować niektóre typowe funkcje do jednej lub więcej aplikacji, które mogą korzystać z tej funkcji. Sprowadza się to do eksportowania klas i funkcji globalnych, które są dostępne dla aplikacji klienckich.

W tym celu należy zapewnić, że każda z funkcji elementów członkowskich jest oznaczona jako import lub eksport. Wymaga to specjalnych `__declspec(dllexport)` deklaracji: i `__declspec(dllimport)`. Gdy klasy są używane przez aplikacje klienckie, chcesz, aby zostały zadeklarowane jako `__declspec(dllimport)`. Gdy sama biblioteka DLL rozszerzenia MFC jest `__declspec(dllexport)`budowana, powinny one być zadeklarowane jako . Ponadto funkcje muszą być faktycznie eksportowane, tak aby programy klienckie wiążą się z nimi w czasie ładowania.

Aby wyeksportować `AFX_EXT_CLASS` całą klasę, użyj w definicji klasy. To makro jest zdefiniowane `__declspec(dllexport)` `_AFXDLL` przez `_AFXEXT` strukturę jako `__declspec(dllimport)` kiedy `_AFXEXT` i jest zdefiniowane, ale zdefiniowane jako, gdy nie jest zdefiniowany. `_AFXEXT`jak opisano powyżej, jest zdefiniowany tylko podczas tworzenia biblioteki DLL rozszerzenia MFC. Przykład:

```cpp
class AFX_EXT_CLASS CExampleExport : public CObject
{ /* ... class definition ... */ };
```

### <a name="not-exporting-the-entire-class"></a>Nie eksportowanie całej klasy

Czasami możesz chcieć wyeksportować tylko poszczególnych niezbędnych członków swojej klasy. Na przykład w przypadku eksportowania klasy pochodnej, `CDialog`może być konieczne tylko `DoModal` wyeksportowanie konstruktora i wywołania. Można wyeksportować tych członków za pomocą biblioteki DLL . DEF, ale można również `AFX_EXT_CLASS` używać w taki sam sposób na poszczególnych członków, które należy wyeksportować.

Przykład:

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

Po wykonaniu tej tej tej pracy może napotkać dodatkowy problem, ponieważ nie są już eksportowania wszystkich członków klasy. Problem polega na tym, że działają makra MFC. Kilka makr pomocnika MFC faktycznie deklaruje lub definiuje elementy członkowskie danych. W związku z tym te elementy członkowskie danych będą również musiały zostać wyeksportowane z biblioteki DLL.

Na przykład makro DECLARE_DYNAMIC jest zdefiniowane w następujący sposób podczas tworzenia biblioteki DLL rozszerzenia MFC:

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
    static CRuntimeClass* PASCAL _GetBaseClass(); \
    public: \
    static AFX_DATA CRuntimeClass class##class_name; \
    virtual CRuntimeClass* GetRuntimeClass() const; \
```

Wiersz, który rozpoczyna `AFX_DATA`się "statyczne" jest deklarowanie obiektu statycznego wewnątrz klasy. Aby poprawnie wyeksportować tę klasę i uzyskać dostęp do informacji o czasie wykonywania z klienta . EXE, należy wyeksportować ten obiekt statyczny. Ponieważ obiekt statyczny jest zadeklarowany `AFX_DATA`za pomocą modyfikatora, wystarczy zdefiniować `AFX_DATA` podczas `__declspec(dllimport)` `__declspec(dllexport)` tworzenia biblioteki DLL i zdefiniować ją tak, jak podczas tworzenia pliku wykonywalnego klienta.

Jak wspomniano powyżej, `AFX_EXT_CLASS` jest już zdefiniowany w ten sposób. Wystarczy ponownie zdefiniować, `AFX_DATA` aby być `AFX_EXT_CLASS` takie same, jak wokół definicji klasy.

Przykład:

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

MFC zawsze używa `AFX_DATA` symbolu na elementach danych, które definiuje w swoich makrach, więc ta technika będzie działać dla wszystkich takich scenariuszy. Na przykład będzie działać dla DECLARE_MESSAGE_MAP.

> [!NOTE]
> Jeśli eksportujesz całą klasę, a nie wybranych członków klasy, elementy członkowskie danych statycznych są eksportowane automatycznie.

Tej samej techniki można użyć `CArchive` do automatycznego wyeksportowania operatora wyodrębniania dla klas, które używają makr DECLARE_SERIAL i IMPLEMENT_SERIAL. Wyeksportuj operator archiwum, przedstawiając nawiasy między deklaracjami klas (znajdującymi się w pliku . H) z następującym kodem:

```cpp
#undef AFX_API
#define AFX_API AFX_EXT_CLASS

/* your class declarations here */

#undef AFX_API
#define AFX_API
```

### <a name="limitations-of-_afxext"></a>Ograniczenia _AFXEXT

Symbol preprocesoru **_AFXEXT** dla bibliotek DLL rozszerzenia MFC można użyć, o ile nie masz wielu warstw dll rozszerzenie MFC. Jeśli masz biblioteki DLL rozszerzenia MFC, które wywołują lub pochodzą z klas w własnych bibliotek dll rozszerzenia MFC, które następnie pochodzą z klas MFC, należy użyć własnego symbolu preprocesora, aby uniknąć niejednoznaczności.

Problem polega na tym, że w Win32 `__declspec(dllexport)` należy jawnie zadeklarować wszelkie dane tak, jakby mają być eksportowane z biblioteki DLL i `__declspec(dllimport)` jeśli ma być importowane z biblioteki DLL. Podczas definiowania `_AFXEXT`, nagłówki MFC `AFX_EXT_CLASS` upewnij się, że jest zdefiniowany poprawnie.

Jeśli masz wiele warstw, jeden `AFX_EXT_CLASS` symbol, taki jak nie jest wystarczający, ponieważ biblioteka DLL rozszerzenia MFC może eksportować nowe klasy, a także importować inne klasy z innej biblioteki DLL rozszerzenia MFC. Aby poradzić sobie z tym problemem, należy użyć specjalnego symbolu preprocesora, który wskazuje, że budujesz samą bibliotekę DLL w porównaniu z przy użyciu biblioteki DLL. Wyobraźmy sobie na przykład dwa biblioteki DLL rozszerzenia MFC, biblioteki DLL i B.DLL. Każdy z nich eksportuje niektóre klasy odpowiednio w A.H i B.H. B.DLL używa klas z biblioteki A.DLL. Pliki nagłówkowe będą wyglądać mniej więcej tak:

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

Po zbudowaniu biblioteki A.DLL jest ona budowana z **/DA_IMPL,** a po zbudowaniu biblioteki B.DLL jest ona zbudowana z **/DB_IMPL**. Przy użyciu oddzielnych symboli dla każdej biblioteki DLL, CExampleB jest eksportowany i CExampleA jest importowany podczas tworzenia B.DLL. CExampleA jest eksportowany podczas tworzenia biblioteki A.DLL i importowane, gdy jest używany przez B.DLL (lub innego klienta).

Tego typu warstw nie można wykonać podczas `AFX_EXT_CLASS` korzystania `_AFXEXT` z wbudowanych i preprocesorowych symboli. Technika opisana powyżej rozwiązuje ten problem w sposób nie w przeciwieństwie do mechanizmu MFC sam używa podczas tworzenia jego OLE, Bazy danych i sieci MFC rozszerzenie bibliotek DLL.

### <a name="not-exporting-the-entire-class"></a>Nie eksportowanie całej klasy

Ponownie, trzeba będzie zwrócić szczególną ostrożność, gdy nie są eksportowanie całej klasy. Należy upewnić się, że niezbędne elementy danych utworzone przez makra MFC są eksportowane poprawnie. Można to zrobić poprzez ponowne `AFX_DATA` zdefiniowanie do konkretnej klasy makro. Należy to zrobić za każdym razem, gdy nie eksportujesz całej klasy.

Przykład:

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

### <a name="dllmain"></a>Dllmain

Poniżej przedstawiono dokładny kod, który należy umieścić w głównym pliku źródłowym dla biblioteki DLL rozszerzenia MFC. Powinien przyjść po standardzie zawiera. Należy zauważyć, że podczas tworzenia plików startowych dla biblioteki DLL `DllMain` rozszerzenia MFC, dostarcza dla Ciebie.

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

Wywołanie `AfxInitExtensionModule` przechwytuje moduły klasy środowiska wykonawczego`CRuntimeClass` (struktury), a także jego`COleObjectFactory` fabryki obiektów (obiekty) `CDynLinkLibrary` do użycia później podczas tworzenia obiektu. (Opcjonalne) wywołanie `AfxTermExtensionModule` umożliwia MFC do czyszczenia biblioteki DLL rozszerzenia MFC, gdy każdy proces odłącza się (co się `FreeLibrary` dzieje, gdy proces kończy działanie lub gdy biblioteka DLL jest zwalniana w wyniku wywołania) z biblioteki DLL rozszerzenia MFC. Ponieważ większość bibliotek DLL rozszerzenia MFC nie są ładowane dynamicznie (zwykle `AfxTermExtensionModule` są one połączone za pośrednictwem bibliotek importu), wywołanie zwykle nie jest konieczne.

Jeśli aplikacja ładuje i zwalnia biblioteki DLL rozszerzenia MFC `AfxTermExtensionModule` dynamicznie, należy wywołać, jak pokazano powyżej. Należy również `AfxLoadLibrary` pamiętać, `AfxFreeLibrary` aby użyć i (zamiast funkcji `LoadLibrary` Win32 i), `FreeLibrary`jeśli aplikacja używa wielu wątków lub jeśli dynamicznie ładuje DLL rozszerzenia MFC. Przy `AfxLoadLibrary` `AfxFreeLibrary` użyciu i zapewnia, że kod uruchamiania i zamykania, który jest wykonywany, gdy biblioteka DLL rozszerzenia MFC jest ładowany i zwalniane nie powoduje uszkodzenia globalnego stanu MFC.

Plik nagłówkowy AFXDLLX. H zawiera specjalne definicje struktur używanych w DLL rozszerzenie MFC, takich jak definicja `AFX_EXTENSION_MODULE` i `CDynLinkLibrary`.

Global *extensionDLL* musi być zadeklarowany, jak pokazano. W przeciwieństwie do 16-bitowej wersji MFC, można przydzielić pamięć i wywołać funkcje MFC w tym `DllMain` czasie, ponieważ MFCxx.DLL jest w pełni zainicjowany przez czas, w którym jest wywoływana.

### <a name="sharing-resources-and-classes"></a>Udostępnianie zasobów i klas

Proste biblioteki DLL rozszerzenia MFC muszą eksportować tylko kilka funkcji o niskiej przepustowości do aplikacji klienckiej i nic więcej. Więcej bibliotek DLL intensywnie korzystających z interfejsu użytkownika może chcieć eksportować zasoby i klasy C++ do aplikacji klienckiej.

Eksportowanie zasobów odbywa się za pośrednictwem listy zasobów. W każdej aplikacji jest pojedynczo `CDynLinkLibrary` połączone listy obiektów. Podczas wyszukiwania zasobu większość standardowych implementacji MFC, które ładują zasoby, najpierw analizuje bieżący moduł zasobów (`AfxGetResourceHandle`) i jeśli nie znaleziono, przechadza się po liście obiektów próbujących `CDynLinkLibrary` załadować żądany zasób.

Dynamiczne tworzenie obiektów C++ o nazwie klasy C++ jest podobne. Mechanizm deserializacji obiektu MFC musi mieć `CRuntimeClass` wszystkie obiekty zarejestrowane, dzięki czemu można go odtworzyć, dynamicznie tworząc obiekt C++ wymaganego typu na podstawie tego, co było przechowywane wcześniej.

Jeśli chcesz, aby aplikacja kliencka używała klas `DECLARE_SERIAL`w dll rozszerzenia MFC, które są , a następnie należy wyeksportować klasy, aby były widoczne dla aplikacji klienckiej. Odbywa się to również `CDynLinkLibrary` przez chodzenie po liście.

W przypadku przykładowego [DLLHUSK](../overview/visual-cpp-samples.md)MFC Advanced Concepts lista wygląda mniej więcej tak:

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

MfCxx.DLL jest zwykle ostatni na liście zasobów i klas. MfCxx.DLL zawiera wszystkie standardowe zasoby MFC, w tym ciągi monitów dla wszystkich standardowych identyfikatorów poleceń. Umieszczenie go w ogonie listy umożliwia bibliotekom DLL i samej aplikacji klienckiej nie posiadanie własnej kopii standardowych zasobów MFC, ale poleganie na zasobach udostępnionych w pliku MFCxx.DLL.

Scalanie zasobów i nazw klas wszystkich bibliotek DLL w przestrzeni nazw aplikacji klienckiej ma tę wadę, że trzeba uważać, jakie identyfikatory lub nazwy wybrać. Oczywiście można wyłączyć tę funkcję, nie eksportując zasobów `CDynLinkLibrary` lub obiektu do aplikacji klienckiej. Przykład [DLLHUSK](../overview/visual-cpp-samples.md) zarządza przestrzenią nazw zasobów udostępnionych przy użyciu wielu plików nagłówkowych. Zobacz [Uwaga techniczna 35,](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) aby uzyskać więcej wskazówek dotyczących korzystania z udostępnionych plików zasobów.

### <a name="initializing-the-dll"></a>Inicjowanie biblioteki DLL

Jak wspomniano powyżej, zwykle chcesz utworzyć `CDynLinkLibrary` obiekt w celu wyeksportowania zasobów i klas do aplikacji klienckiej. Aby zainicjować bibliotekę DLL, należy podać wyeksportowany punkt wejścia. Minimalnie jest to procedura void, która nie ma argumentów i nic nie zwraca, ale może to być wszystko, co lubisz.

Każda aplikacja kliencka, która chce używać biblioteki DLL musi wywołać tę procedurę inicjowania, jeśli używasz tej metody. Można również przydzielić `CDynLinkLibrary` ten `DllMain` obiekt `AfxInitExtensionModule`w swoim tuż po wywołaniu .

Procedura inicjowania `CDynLinkLibrary` musi utworzyć obiekt w stercie bieżącej aplikacji, podłączone do informacji DLL rozszerzenia MFC. Można to zrobić za pomocą następujących czynności:

```cpp
extern "C" extern void WINAPI InitXxxDLL()
{
    new CDynLinkLibrary(extensionDLL);
}
```

Rutynowa nazwa *InitXxxDLL* w tym przykładzie może być wszystkim, co chcesz. Nie musi być **extern "C",** ale w ten sposób sprawia, że lista eksportu łatwiejsze do utrzymania.

> [!NOTE]
> Jeśli używasz biblioteki DLL rozszerzenia MFC z zwykłej biblioteki DLL MFC, należy wyeksportować tę funkcję inicjowania. Ta funkcja musi być wywoływana z zwykłej biblioteki DLL MFC przed użyciem jakichkolwiek klas lub zasobów DLL rozszerzenia MFC.

### <a name="exporting-entries"></a>Eksportowanie wpisów

Prosty sposób eksportowania klas jest `__declspec(dllimport)` `__declspec(dllexport)` użycie i na każdej klasie i funkcji globalnej, które chcesz wyeksportować. To sprawia, że o wiele łatwiejsze, ale jest mniej wydajne niż nazewnictwo każdego punktu wejścia (opisane poniżej), ponieważ masz mniejszą kontrolę nad tym, jakie funkcje są eksportowane i nie można eksportować funkcji przez porządkowe. TESTDLL1 i TESTDLL2 używają tej metody do eksportowania swoich wpisów.

Bardziej efektywną metodą (i metodą stosowaną przez MFCxx.DLL) jest eksportowanie każdego wpisu ręcznie przez nadanie nazwy każdemu wpisowi w pliku . def. Ponieważ eksportujemy selektywny eksport z naszej biblioteki DLL (czyli nie wszystkiego), musimy zdecydować, które konkretne interfejsy chcemy eksportować. Jest to trudne, ponieważ należy określić zniekształcone nazwy do konsolidatora w postaci wpisów w pliku . def. Nie eksportuj żadnych klas C++, chyba że naprawdę musisz mieć dla niej dowiązanie symboliczne.

Jeśli próbowano eksportować klasy języka C++ za pomocą pliku . DEF przed, można opracować narzędzie do automatycznego generowania tej listy. Można to zrobić za pomocą dwuetapowego procesu łącza. Połącz bibliotekę DLL raz bez eksportu i pozwól konsolidatorowi wygenerować plik . MAP. Tthe. Plik MAP może służyć do generowania listy funkcji, które powinny być eksportowane, więc z pewnymi przegrupowania, może służyć do generowania wpisów EXPORT dla . def. Lista eksportu dla MFCxx.DLL i OLE i Database MFC rozszerzenie DLL, kilka tysięcy w liczbie, został wygenerowany z takim procesem (chociaż nie jest całkowicie automatyczne i wymaga pewnego dostrajania strony co jakiś czas).

### <a name="cwinapp-vs-cdynlinklibrary"></a>CWinApp vs. CDynLinkLibrary

Biblioteka DLL rozszerzenia MFC `CWinApp`nie ma własnego obiektu pochodnego; zamiast tego musi pracować `CWinApp`z obiektem pochodnym aplikacji klienckiej. Oznacza to, że aplikacja kliencka jest właścicielem pompy wiadomości głównej, pętli bezczynnej i tak dalej.

Jeśli biblioteka DLL rozszerzenia MFC musi zachować dodatkowe dane dla `CDynLinkLibrary` każdej aplikacji, można wyprowadzić nową klasę z i utworzyć ją w procedurze InitXxxDLL opisać powyżej. Po uruchomieniu biblioteki DLL można sprawdzić listę `CDynLinkLibrary` obiektów bieżącej aplikacji, aby znaleźć jedną dla tej konkretnej biblioteki DLL rozszerzenia MFC.

### <a name="using-resources-in-your-dll-implementation"></a>Korzystanie z zasobów we implementacji biblioteki DLL

Jak wspomniano powyżej, domyślne obciążenie zasobów `CDynLinkLibrary` będzie chodzić listę obiektów poszukujących pierwszego EXE lub DLL, który ma żądany zasób. Wszystkie interfejsy API MFC, a także `AfxFindResourceHandle` wszystkie wewnętrzne kody używa do przejścia listy zasobów, aby znaleźć dowolny zasób, bez względu na to, gdzie może znajdować się.

Jeśli chcesz załadować tylko zasoby z określonego miejsca, `AfxGetResourceHandle` `AfxSetResourceHandle` użyj interfejsów API i zapisać stary uchwyt i ustawić nowy uchwyt. Pamiętaj, aby przywrócić stary dojście do zasobu przed powrotem do aplikacji klienckiej. Przykładowy TESTDLL2 używa tej metody jawnie ładowania menu.

Przechodzenie z listy ma wady, że jest nieco wolniejszy i wymaga zarządzania zakresami identyfikatorów zasobów. Ma tę zaletę, że aplikacja kliencka, która łączy się z kilkoma bibliotekami DLL rozszerzenia MFC, może używać dowolnego zasobu dostarczonego przez bibliotekę DLL bez konieczności określania dojścia wystąpienia biblioteki DLL. `AfxFindResourceHandle`jest interfejsem API używanym do przechodzenia z listy zasobów w celu wyszukynia danego dopasowania. Przyjmuje nazwę i typ zasobu i zwraca dojście zasobu, do którego został znaleziony po raz pierwszy (lub NULL).

## <a name="writing-an-application-that-uses-the-dll-version"></a><a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Pisanie aplikacji korzystającej z wersji DLL

### <a name="application-requirements"></a>Wymagania dotyczące aplikacji

Aplikacja, która używa udostępnionej wersji MFC musi przestrzegać kilku prostych reguł:

- Musi mieć `CWinApp` obiekt i przestrzegać standardowych reguł dla pompy wiadomości.

- Musi być skompilowany z zestawem wymaganych flag kompilatora (patrz poniżej).

- Musi łączyć się z bibliotekami importu MFCxx. Ustawiając flagi kompilatora wymagane, nagłówki MFC określić w czasie łącza, które biblioteki aplikacji należy połączyć z.

- Aby uruchomić plik wykonywalny, mfCxx.DLL musi znajdować się na ścieżce lub w katalogu systemu Windows.

### <a name="building-with-the-development-environment"></a>Budowanie ze środowiskiem deweloperskim

Jeśli używasz wewnętrznego pliku makefile z większością standardowych ustawień domyślnych, możesz łatwo zmienić projekt, aby utworzyć wersję biblioteki DLL.

W poniższym kroku przyjęto założenie, że masz poprawnie działającą aplikację MFC połączoną z NAFXCWD. LIB (do debugowania) i NAFXCW. LIB (dla sprzedaży detalicznej) i chcesz go przekonwertować na używaj udostępnionej wersji biblioteki MFC. Korzystasz ze środowiska Visual C++ i masz wewnętrzny plik projektu.

1. W menu **Projekty** kliknij polecenie **Właściwości**. Na stronie **Ogólne** w obszarze **Domyślne programy project(ustawienia)** ustaw klasy programu Microsoft Foundation na **używanie MFC w udostępnionej biblioteki DLL** (MFCxx(d).dll).

### <a name="building-with-nmake"></a>Budynek z NMAKE

Jeśli używasz funkcji external makefile programu Visual C++ lub używasz NMAKE bezpośrednio, musisz edytować plik makefile do obsługi opcji kompilatora i konsolidatora

Wymagane flagi kompilatora:

- **/D_AFXDLL /MD**
   **/D_AFXDLL**

Standardowe nagłówki MFC wymagają zdefiniowania tego symbolu:

- **/MD** Aplikacja musi używać wersji DLL biblioteki czasu wykonywania języka C

Wszystkie inne flagi kompilatora wykonaj domyślne wartości MFC (na przykład _DEBUG do debugowania).

Edytuj listę bibliotek konsolidatora. Zmień NAFXCWD. LIB na MFCxxD.LIB i zmień NAFXCW. LIB do MFCxx.LIB. Zamień libc. LIB z MSVCRT. Lib. Podobnie jak w przypadku każdej innej biblioteki MFC, ważne jest, aby mfcxxd.LIB był umieszczany **przed** dowolnymi bibliotekami środowiska wykonawczego C.

Opcjonalnie dodaj **/D_AFXDLL** do opcji kompilatora zasobów detalicznych i debugowania (ten, który faktycznie kompiluje zasoby z **/R**). Dzięki temu ostateczny plik wykonywalny jest mniejszy, udostępniając zasoby, które są obecne w bibliotekach DLL MFC.

Po dokonaniu tych zmian wymagana jest pełna przebudowa.

### <a name="building-the-samples"></a>Tworzenie próbek

Większość przykładowych programów MFC można tworzyć z programu Visual C++ lub z udostępnionego pliku MAKEFILE zgodnego z NMAKE z wiersza polecenia.

Aby przekonwertować dowolną z tych próbek do użycia mfcxx.DLL, można załadować plik . MAK w języku Visual C++ i ustawić opcje projektu, jak opisano powyżej. Jeśli używasz kompilacji NMAKE, można określić "AFXDLL = 1" w wierszu polecenia NMAKE i że będzie tworzyć próbki przy użyciu udostępnionych bibliotek MFC.

Przykładowy [DLLHUSK](../overview/visual-cpp-samples.md) MFC Advanced Concepts jest zbudowany z wersji DLL MFC. Ten przykład nie tylko ilustruje sposób tworzenia aplikacji połączonych z mfcxx.DLL, ale także ilustruje inne funkcje opcji pakowania bibliotek DLL MFC, takie jak biblioteki DLL rozszerzenia MFC opisane w dalszej części tej uwagi technicznej.

### <a name="packaging-notes"></a>Uwagi dotyczące opakowań

Wersja detaliczna bibliotek DLL (MFCxx[U]. DLL) są swobodnie redystrybucyjne. Wersja debugowania bibliotek DLL nie są swobodnie redystrybucyjne i powinny być używane tylko podczas tworzenia aplikacji.

Biblioteki DLL debugowania są dostarczane z informacjami debugowania. Za pomocą debugera języka Visual C++, można śledzić wykonanie aplikacji, a także biblioteki DLL. Biblioteki DLL wydania (MFCxx[U]. DLL) nie zawierają informacji debugowania.

Jeśli dostosujesz lub odbudujesz biblioteki DLL, należy wywołać je coś innego niż "MFCxx" Plik MFC SRC MFCDLL. Klucz MAK opisuje opcje kompilacji i zawiera logikę zmiany nazwy biblioteki DLL. Zmiana nazwy plików jest konieczne, ponieważ te biblioteki DLL są potencjalnie współużytkowane przez wiele aplikacji MFC. Posiadanie niestandardowej wersji bibliotek DLL MFC zastąpić te zainstalowane w systemie może przerwać inną aplikację MFC przy użyciu udostępnionych bibliotek DLL MFC.

Nie zaleca się przebudowy bibliotek DLL MFC.

## <a name="how-the-mfcxxdll-is-implemented"></a><a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Jak implementuje mfcxx.DLL

W poniższej sekcji opisano sposób implementacji biblioteki DLL MFC (MFCxx.DLL i MFCxxD.DLL). Zrozumienie szczegółów w tym miejscu również nie są ważne, jeśli wszystko, co chcesz zrobić, to użyć biblioteki DLL MFC z aplikacją. Szczegóły w tym miejscu nie są niezbędne do zrozumienia, jak napisać bibliotekę DLL rozszerzenia MFC, ale zrozumienie tej implementacji może pomóc w napisaniu własnej biblioteki DLL.

### <a name="implementation-overview"></a>Omówienie implementacji

Biblioteka DLL MFC jest naprawdę szczególny przypadek biblioteki DLL rozszerzenia MFC, jak opisano powyżej. Ma bardzo dużą liczbę eksportu dla dużej liczby klas. Istnieje kilka dodatkowych rzeczy, które robimy w MFC DLL, które sprawiają, że nawet bardziej wyjątkowy niż regularne rozszerzenie MFC DLL.

### <a name="win32-does-most-of-the-work"></a>Win32 wykonuje większość pracy

16-bitowa wersja MFC potrzebne szereg specjalnych technik, w tym danych na aplikację w segmencie stosu, specjalne segmenty utworzone przez niektóre 80x86 kod zestawu, konteksty wyjątków na proces i inne techniki. Win32 bezpośrednio obsługuje dane na proces w dll, który jest to, co chcesz przez większość czasu. W przeważającej części MFCxx.DLL to tylko NAFXCW. LIB w pakiecie z biblioteką DLL. Jeśli spojrzysz na kod źródłowy MFC, znajdziesz bardzo niewiele #ifdef _AFXDLL, ponieważ istnieje bardzo niewiele specjalnych przypadków, które należy wykonać. Specjalne przypadki, które są tam są specjalnie do czynienia z Win32 w systemie Windows 3.1 (inaczej znany jako Win32s). Win32s nie obsługuje danych DLL dla procesu bezpośrednio, więc biblioteka DLL MFC musi używać interfejsów API win32 magazynu lokalnego wątku (TLS) do uzyskiwania danych lokalnych procesu.

### <a name="impact-on-library-sources-additional-files"></a>Wpływ na źródła biblioteki, dodatkowe pliki

Wpływ **_AFXDLL** wersji na normalne źródła biblioteki klas MFC i nagłówki jest stosunkowo niewielki. Istnieje specjalny plik wersji (AFXV_DLL. H) oraz dodatkowy plik nagłówka (AFXDLL_. H) zawarte przez główny AFXWIN. Nagłówek H. The AFXDLL_. H nagłówek `CDynLinkLibrary` zawiera klasy i inne `_AFXDLL` szczegóły implementacji zarówno aplikacji i bibliotek DLL rozszerzenia MFC. The AFXDLLX. Nagłówek H jest przeznaczony do tworzenia bibliotek DLL rozszerzenia MFC (szczegóły powyżej znajdują się powyżej).

Regularne źródła do biblioteki MFC w MFC SRC mają `_AFXDLL` jakiś dodatkowy kod warunkowy w ramach #ifdef. Dodatkowy plik źródłowy (DLLINIT. CPP) zawiera dodatkowy kod inicjowania biblioteki DLL i inny klej dla udostępnionej wersji MFC.

Aby utworzyć udostępnioną wersję MFC, dodatkowe pliki są dostarczane. (Zobacz poniżej, aby uzyskać szczegółowe informacje na temat tworzenia biblioteki DLL.)

- Dwa. Pliki DEF są używane do eksportowania punktów wejścia MFC DLL do debugowania (MFCxxD.DEF) i wersji (MFCxx.DEF) wersji biblioteki DLL.

- An . RC (MFCDLL. RC) zawiera wszystkie standardowe zasoby MFC i zasób VERSIONINFO dla biblioteki DLL.

- A. CLW (MFCDLL. CLW) jest w celu umożliwienia przeglądania klas MFC przy użyciu ClassWizard. Uwaga: ta funkcja nie jest szczególnie charakterystyczna dla wersji DLL MFC.

### <a name="memory-management"></a>Zarządzanie pamięcią

Aplikacja korzystająca z biblioteki MFCxx.DLL używa wspólnego przydziału pamięci dostarczonego przez bibliotekę DLL MSVCRTxx.DLL, udostępnionej biblioteki DLL środowiska C. Aplikacja, wszelkie biblioteki DLL rozszerzenia MFC i biblioteki DLL MFC same używają tego udostępnionego przydziału pamięci. Za pomocą udostępnionej biblioteki DLL do alokacji pamięci bibliotek bibliotek DLL MFC można przydzielić pamięć, która jest później zwolniona przez aplikację lub odwrotnie. Ponieważ zarówno aplikacja, jak i biblioteka DLL muszą używać tego samego alokatora, nie należy zastępować **nowego operatora** globalnego C++ ani **usuwania operatora.** Te same zasady mają zastosowanie do pozostałych procedur alokacji pamięci w czasie wykonywania języka C (takich jak **malloc**, **realloc**, **free**i inne).

### <a name="ordinals-and-class-__declspecdllexport-and-dll-naming"></a>Liczby porządkowe i __declspec klasy(dllexport) i nazewnictwo biblioteki DLL

Nie używamy `class` funkcji **__declspec(dllexport)** kompilatora C++. Zamiast tego lista eksportu jest dołączona do źródeł biblioteki klas (MFCxx.DEF i MFCxxD.DEF). Eksportowane są tylko te wybrane punkty wejścia (funkcje i dane). Inne symbole, takie jak funkcje implementacji prywatnej MFC lub klasy, nie są eksportowane Wszystkie eksporty są wykonywane przez porządkowe bez nazwy ciągu w tabeli nazw rezydentnych lub nierezydentów.

Korzystanie `class` z **__declspec(dllexport)** może być realną alternatywą dla tworzenia mniejszych bibliotek DLL, ale w przypadku dużych bibliotek DLL, takich jak MFC, domyślny mechanizm eksportowania ma limity wydajności i pojemności.

Co to wszystko oznacza, że możemy spakować dużą ilość funkcji w wydaniu MFCxx.DLL, który jest tylko około 800 KB bez narażania dużo wykonywania lub szybkości ładowania. MFCxx.DLL byłby większy o 100K, gdyby ta technika nie została wykorzystana. Umożliwia to również dodanie dodatkowych punktów wejścia na końcu pliku . DEF, aby umożliwić proste przechowywanie wersji bez uszczerbku dla szybkości i wydajności rozmiaru eksportu przez porządkowe. Główne wersje wersji w bibliotece klas MFC zmieni nazwę biblioteki. Oznacza to, że MFC30. DLL jest redystrybucyjny biblioteki DLL zawierającej wersję 3.0 biblioteki klas MFC. Uaktualnienie tej biblioteki DLL, powiedzmy, w hipotetycznym MFC 3.1, biblioteka DLL będzie nazywać się MFC31. Zamiast tego biblioteka DLL. Ponownie, jeśli zmodyfikujesz kod źródłowy MFC do produkcji niestandardowej wersji biblioteki DLL MFC, należy użyć innej nazwy (i najlepiej jeden bez "MFC" w nazwie).

## <a name="see-also"></a>Zobacz też

[Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)<br/>
[Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)
