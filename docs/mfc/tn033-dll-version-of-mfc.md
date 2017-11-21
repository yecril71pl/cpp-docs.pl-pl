---
title: 'TN033: Wersja dll biblioteki MFC | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.dll
dev_langs: C++
helpviewer_keywords:
- MFC DLLs [MFC], writing MFC extension DLLS
- AFXDLL library
- DLLs [MFC], MFC
- DLL version of MFC [MFC]
- TN033
ms.assetid: b6f1080b-b66b-4b1e-8fb1-926c5816392c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb1fb4094e5a54f82aa6aeebffe576965838cf7e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="tn033-dll-version-of-mfc"></a>TN033: wersja DLL biblioteki MFC
Ta uwaga opisano, jak można użyć MFCxx.DLL i MFCxxD.DLL (gdzie x jest numerem wersji MFC) udostępniane biblioteki dołączanej dynamicznie aplikacji MFC i biblioteki DLL rozszerzeń MFC. Aby uzyskać więcej informacji na temat regularne biblioteki DLL MFC, zobacz [za pomocą MFC jako części biblioteki DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
 Ta uwaga techniczna obejmuje trzy aspekty biblioteki dll. Ostatnie dwa są bardziej zaawansowanym użytkownikom:  
  
- [Jak utworzyć biblioteki DLL rozszerzenia MFC](#_mfcnotes_how_to_write_an_mfc_extension_dll)  
  
- [Sposób tworzenia aplikacji MFC, która używa wersja dll biblioteki MFC](#_mfcnotes_writing_an_application_that_uses_the_dll_version)  
  
- [Jak MFC DLL biblioteki udostępnione są implementowane.](#_mfcnotes_how_the_mfc30.dll_is_implemented)  
  
 Jeśli interesuje Cię Tworzenie biblioteki DLL przy użyciu MFC, która może być używany z innego typu niż MFC aplikacji (jest to nazywane regularną bibliotekę DLL MFC), zapoznaj się [11 Uwaga techniczna](../mfc/tn011-using-mfc-as-part-of-a-dll.md).  
  
## <a name="overview-of-mfcxxdll-support-terminology-and-files"></a>Omówienie obsługi MFCxx.DLL: terminologii i plików  
 **Regularne biblioteki DLL MFC**: Użyj regularną bibliotekę DLL MFC do tworzenia biblioteki DLL autonomicznej niektórych klas MFC. Interfejsy granicy aplikacji/DLL są interfejsy "C", a aplikacja kliencka nie musi być aplikacji MFC.  
  
 Jest to wersja obsługiwana w wersji 1.0 MFC Obsługa DLL. Opisano w [11 Uwaga techniczna](../mfc/tn011-using-mfc-as-part-of-a-dll.md) i przykładowa pojęcia zaawansowane MFC [DLLScreenCap](../visual-cpp-samples.md).  
  
> [!NOTE]
>  Począwszy od programu Visual C++ w wersji 4.0 termin **USRDLL** jest przestarzałe i zostało zastąpione przez regularne biblioteki DLL MFC, która łączy statycznie z MFC. Regularne biblioteki DLL MFC, która łączy dynamicznie z MFC mogą również kompilacji.  
  
 MFC 3.0 (lub nowszym) obsługuje regularne biblioteki DLL MFC z nowych funkcji, łącznie z klas OLE i bazy danych.  
  
 **AFXDLL**: to jest również nazywany udostępnionego wersji biblioteki MFC. Jest to nowa funkcja obsługi DLL dodane w MFC 2.0. Samej biblioteki MFC jest liczba bibliotek DLL (opisanych poniżej) i dynamicznie łączy bibliotek DLL, które wymaga aplikacji klienta lub DLL. Interfejsy granicy aplikacji/DLL są C + +/ interfejsy klas MFC. Aplikacja kliencka musi być aplikacji MFC. Obejmuje to obsługę wszystkich funkcji MFC 3.0 (wyjątek: UNICODE nie jest obsługiwane dla klas baz danych).  
  
> [!NOTE]
>  Począwszy od programu Visual C++ w wersji 4.0 tego rodzaju biblioteki DLL jest określany jako "Rozszerzenie pliku DLL."  
  
 Ta uwaga będzie używana MFCxx.DLL do odwoływania się do całej biblioteki MFC DLL zestawu, w tym:  
  
-   Debugowanie: MFCxxD.DLL (połączone) i MFCSxxD.LIB (statyczny).  
  
-   Wersja: MFCxx.DLL (połączone) i MFCSxx.LIB (statyczny).  
  
-   Debugowanie Unicode: MFCxxUD.DLL (połączone) i MFCSxxD.LIB (statyczny).  
  
-   Wersja Unicode: MFCxxU.DLL (połączone) i MFCSxxU.LIB (statyczny).  
  
> [!NOTE]
>  MFCSxx [N] [D]. Biblioteki LIB są używane w połączeniu z MFC udostępnione biblioteki dll. Te biblioteki zawierają kod, który musi być połączone statycznie z aplikacji lub DLL.  
  
 Łącza aplikacji do odpowiedniej biblioteki importu:  
  
-   Debugowanie: MFCxxD.LIB  
  
-   Wersja: MFCxx.LIB  
  
-   Unicode debugowania: MFCxxUD.LIB  
  
-   Wersja Unicode: MFCxxU.LIB  
  
 "Rozszerzenie biblioteki DLL MFC" jest oparty na MFCxx.DLL biblioteki DLL (i/lub innych MFC udostępnionych bibliotek DLL). W tym miejscu Architektura składników MFC jest uruchamiane. Jeśli pochodzi z klasy MFC przydatne klasy lub kompilacji innego toolkit przypominającej MFC, można umieścić go w bibliotece DLL. Biblioteka DLL używa MFCxx.DLL, tak jak w przypadku aplikacji klienckiej ultimate. Pozwala to na klas liścia wielokrotnego użytku, może być ponownie używane klasy podstawowe i klasy wielokrotnego użytku widoku/dokumentów.  
  
## <a name="pros-and-cons"></a>Zalet i wad  
 Dlaczego należy używać udostępnionych wersja MFC  
  
-   Przy użyciu biblioteki udostępnionej może powodować mniejsze aplikacji (minimalnego aplikacji, która używa większość biblioteki MFC jest mniejsza niż 10 KB).  
  
-   Wersja udostępnionego MFC obsługuje biblioteki DLL rozszerzenia MFC i regularne biblioteki DLL MFC.  
  
-   Tworzenie aplikacji korzystającej z udostępnionej biblioteki MFC jest szybsze od tworzenia aplikacji statycznie połączone MFC, ponieważ nie jest konieczne łączenie MFC sam. Jest to szczególnie istotne w **debugowania** kompilacji, w którym konsolidator musi compact informacje o debugowaniu — przez łączenie z biblioteki DLL, który już zawiera informacje o debugowaniu, jest mniej informacji debugowania kompaktowania w aplikacji.  
  
 Dlaczego należy nie należy używać udostępnionych wersja MFC:  
  
-   Wysyłanie aplikacji, która używa biblioteki współużytkowanej wymaga dostarczany MFCxx.DLL (i inne) biblioteki w programie. MFCxx.DLL jest dystrybuowany za darmo do dystrybucji, takich jak wiele bibliotek DLL, ale nadal należy zainstalować biblioteki DLL programu Instalatora. Ponadto muszą dostarczać MSVCRTxx.DLL, zawierający biblioteki C runtime, który jest używany zarówno przez Twojego programu oraz biblioteki DLL MFC, samodzielnie.  
  
##  <a name="_mfcnotes_how_to_write_an_mfc_extension_dll"></a>Jak napisać bibliotekę DLL rozszerzenia MFC  
 Biblioteka DLL rozszerzenia MFC jest biblioteki DLL zawierającej klasy i funkcje zapisane wzbogacać funkcji klas MFC. Biblioteka DLL rozszerzenia MFC używa udostępnionej biblioteki MFC dll w taki sam sposób jak aplikacja używa, kilka dodatkowe zagadnienia:  
  
-   Proces kompilacji jest podobny do tworzenia aplikacji, która używa udostępnionej biblioteki MFC z kilku dodatkowych kompilatora i opcje konsolidatora.  
  
-   Biblioteka DLL rozszerzenia MFC nie ma `CWinApp`-klasy.  
  
-   Biblioteka DLL rozszerzenia MFC podać specjalnego `DllMain`. Dostarcza kreatorami AppWizard `DllMain` funkcji, które można modyfikować.  
  
-   Biblioteka DLL rozszerzenia MFC zapewniają zazwyczaj procedura inicjowania, aby utworzyć **CDynLinkLibrary** Jeśli rozszerzeń MFC DLL chce wyeksportować `CRuntimeClass`es lub zasobów do aplikacji. Klasy pochodnej z **CDynLinkLibrary** mogą być używane, jeśli dane poszczególnych aplikacji, muszą zostać zachowane przez bibliotekę DLL rozszerzenia MFC.  
  
 Te zagadnienia są opisane bardziej szczegółowo poniżej. Należy również dotyczyć próbki pojęcia zaawansowane MFC [DLLHUSK](../visual-cpp-samples.md) ponieważ zastosowano:  
  
-   Kompilowanie aplikacji przy użyciu bibliotek udostępnionych. (DLLHUSK. EXE jest aplikacji MFC, która dynamicznie łącza do biblioteki MFC dll, jak również inne).  
  
-   Tworzenie biblioteki DLL rozszerzenia MFC. (Należy pamiętać flagi specjalnych, takich jak `_AFXEXT` używane w tworzenie biblioteki DLL rozszerzenia MFC)  
  
-   Dwa przykłady biblioteki DLL rozszerzenia MFC. Przedstawia jedną podstawową strukturę biblioteki DLL rozszerzenia MFC z ograniczoną eksportu (TESTDLL1) i innych programów eksportowania całej klasy interfejsu (TESTDLL2).  
  
 Zarówno aplikacja klienta, jak i wszystkie biblioteki DLL rozszerzeń MFC musi używać tej samej wersji MFCxx.DLL. Należy postępować zgodnie z Konwencją biblioteki MFC DLL i podaj zarówno debugowania i sprzedaży detalicznej (/ release) wersja bibliotekę DLL rozszerzenia MFC. Pozwala to na programów klienckich do kompilacji zarówno debugowania, jak i detalicznej wersji aplikacji, a następnie połącz je z odpowiednich debugowania lub wersji detalicznej wszystkie biblioteki dll.  
  
> [!NOTE]
>  Ponieważ C++ nazwa przekręcona i wyeksportować problemów, na liście eksportu z biblioteki DLL rozszerzenia MFC może być różna debugowania i detalicznej wersji tego samego pliku dll i biblioteki DLL dla różnych platform. Detaliczne MFCxx.DLL ma około 2000 wyeksportowane punktów wejścia. Debuguj MFCxxD.DLL ma około 3000 wyeksportowane punktów wejścia.  
  
### <a name="quick-note-on-memory-management"></a>Szybkie uwagi dotyczące zarządzania pamięcią  
 Sekcji "Zarządzania pamięcią," zbliża się koniec tej uwagi techniczne, w tym artykule opisano implementacja MFCxx.DLL wersją udostępnionego MFC. Informacje potrzebne do wdrożenia po prostu rozszerzenia MFC DLL jest opisane w tym miejscu.  
  
 MFCxx.DLL i wszystkie rozszerzenia biblioteki DLL MFC załadowane do przestrzeni adresowej aplikacji klienta będzie używać tego samego alokatora, ładowanie zasobów i innych stanów "globalne" MFC tak, jakby były w tej samej aplikacji. Jest to istotne, ponieważ biblioteki z systemem innym niż MFC DLL i regularne biblioteki DLL MFC, która łączy statycznie z MFC nie dokładnym przeciwieństwem i mieć każdej biblioteki DLL przydziału poza własną pulę pamięci.  
  
 Jeśli bibliotekę DLL rozszerzenia MFC przydziela pamięć, pamięci, można swobodnie intermix z innym obiektem przydzielone aplikacji. Ponadto jeśli wystąpiła awaria aplikacji korzystającej z udostępnionej biblioteki MFC, ochrona systemu operacyjnego Obsługa integralność innych aplikacji MFC, udostępnianie biblioteki DLL.  
  
 Podobnie innych stanów "globalne" MFC, jak bieżący plik wykonywalny do ładowania zasobów, są również współużytkowane aplikacji klienckiej i wszystkie biblioteki DLL rozszerzenia MFC także MFCxx.DLL się.  
  
### <a name="building-an-mfc-extension-dll"></a>Tworzenie biblioteki DLL rozszerzenia MFC  
 Kreatorami AppWizard umożliwia utworzenie projektu biblioteki DLL rozszerzenia MFC, i automatycznie wygeneruje odpowiedni kompilatora i ustawienia konsolidatora. Był wygenerować także `DllMain` funkcji, które można modyfikować.  
  
 Jeśli istniejącego projektu są konwertowane na bibliotekę DLL rozszerzenia MFC, uruchom przy użyciu standardowych reguł do tworzenia aplikacji korzystających z udostępnionych wersji MFC, a następnie wykonaj następujące czynności:  
  
-   Dodaj **/D_AFXEXT** do flagi kompilatora. W oknie dialogowym właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię preprocesora. Dodaj `_AFXEXT` do pola Definiowanie makr oddzielając każdy z elementów średnikami.  
  
-   Usuń **/Gy** przełącznika kompilatora. W oknie dialogowym właściwości projektu wybierz węzeł C/C++. Następnie wybierz kategorię generowania kodu. Upewnij się, że opcja "Włącz funkcję łączenia na poziomie" nie jest włączona. Ułatwi wyeksportować klasy, ponieważ konsolidator nie spowoduje usunięcia funkcji bez odwołań. Jeśli oryginalny projekt jest używany do tworzenia zwykły biblioteki MFC DLL połączone statycznie z MFC, zmień **/MT [d]** — opcja kompilatora do **/ / MD [d]**.  
  
-   Tworzenie eksportu biblioteki z **/dll** możliwość łącza. Spowoduje to ustawienie podczas tworzenia nowego docelowego, określanie biblioteki dołączanej Win32 jako typ docelowy.  
  
### <a name="changing-your-header-files"></a>Zmiana pliki nagłówka  
 Celem rozszerzenia MFC DLL jest zwykle można wyeksportować niektóre typowe funkcje do co najmniej jednej aplikacji, które mogą używać tej funkcji. To wrzała w dół do eksportowania klasy i funkcje globalne, które są dostępne dla aplikacji klienckich.  
  
 W tym celu należy upewnić się, że każda z funkcji Członkowskich jest oznaczony jako importowania lub eksportowania zależnie od potrzeb. Wymaga to specjalne deklaracje: **__declspec(dllexport)** i **__declspec(dllimport)**. W przypadku używania przez aplikacje klienckie klas mają być zadeklarowany jako **__declspec(dllimport)**. Podczas tworzenia rozszerzenia MFC DLL sam powinien być zadeklarowany jako **__declspec(dllexport)**. Ponadto funkcji musi być faktycznie eksportowany, dzięki czemu programy klienckie powiązać je w czasie ładowania.  
  
 Aby wyeksportować klasie całego, należy użyć **afx_ext_class —** w definicji klasy. To makro jest definiowana za pomocą framework jako **__declspec(dllexport)** podczas **_AFXDLL** i `_AFXEXT` jest zdefiniowany, ale zdefiniowany jako **__declspec(dllimport)** podczas `_AFXEXT` nie jest zdefiniowany. `_AFXEXT`jak opisano powyżej, jest zdefiniowana tylko podczas kompilowania bibliotekę DLL rozszerzenia MFC. Na przykład:  
  
```  
class AFX_EXT_CLASS CExampleExport : public CObject  
{ ... class definition ... };  
```  
  
### <a name="not-exporting-the-entire-class"></a>Nie eksportowania całej klasy  
 Czasami można wyeksportować tylko poszczególne elementy niezbędne klasy. Na przykład w przypadku eksportowania `CDialog`-klasy, może być tylko należy wyeksportować konstruktora i `DoModal` wywołania. Możesz wyeksportować tych elementów członkowskich za pomocą biblioteki DLL. Plik DEF, ale można również użyć **afx_ext_class —** w podobny sposób na poszczególnych członków, należy wyeksportować.  
  
 Na przykład:  
  
```  
class CExampleDialog : public CDialog  
{  
public:  
    AFX_EXT_CLASS CExampleDialog();
AFX_EXT_CLASS int DoModal();
*// rest of class definition  
 .  
 .  
 .  
};  
```  
  
 Po wykonaniu tej czynności może wystąpić problem dodatkowe ponieważ wszystkie elementy członkowskie klasy nie są eksportowane. Problem jest w ten sposób pracy makr MFC. Kilka makra pomocnika MFC faktycznie zadeklarować lub Zdefiniuj elementy członkowskie danych. W związku z tym te elementy członkowskie danych również należy wyeksportować z biblioteki DLL.  
  
 Na przykład `DECLARE_DYNAMIC` podczas tworzenia biblioteki DLL rozszerzenia MFC — makro jest zdefiniowane w następujący sposób:  
  
```  
#define DECLARE_DYNAMIC(class_name) \  
protected: \  
    static CRuntimeClass* PASCAL _GetBaseClass();

\  
    public: \  
    static AFX_DATA CRuntimeClass class##class_name; \  
    virtual CRuntimeClass* GetRuntimeClass() const;

\  
```  
  
 Wiersz rozpoczynający się "statyczne `AFX_DATA`" jest deklarowanie obiektu statycznego wewnątrz klasy. Aby wyeksportować ta klasa poprawnie i uzyskać dostęp do informacji środowiska uruchomieniowego od klienta. EXE, należy wyeksportować tego obiektu statycznego. Ponieważ obiektu statycznego jest zadeklarowana z modyfikatorem `AFX_DATA`, musisz zdefiniować `AFX_DATA` jako **__declspec(dllexport)** podczas tworzenia biblioteki DLL i zdefiniować ją jako **__declspec(dllimport)** podczas kompilowania pliku wykonywalnego klienta.  
  
 Jak wspomniano powyżej, **afx_ext_class —** jest już zdefiniowany w ten sposób. Wystarczy zdefiniować ponownie `AFX_DATA` być taka sama jak **afx_ext_class —** wokół definicję klasy.  
  
 Na przykład:  
  
```  
#undef  AFX_DATA  
#define AFX_DATA AFX_EXT_CLASS  
class CExampleView : public CView  
{  
    DECLARE_DYNAMIC() *// ... class definition ...  
};  
#undef  AFX_DATA  
#define AFX_DATA  
```  
  
 Zawsze używa MFC `AFX_DATA` symbolu definiuje w makrach, więc ta metoda będzie działać we wszystkich tych scenariuszach elementów danych. Na przykład, będzie działać dla `DECLARE_MESSAGE_MAP`.  
  
> [!NOTE]
>  Eksportowania całej klasy, a nie zaznaczone elementy członkowskie klasy statyczne elementy członkowskie danych automatycznie są eksportowane.  
  
 Tę samą metodę umożliwia automatyczne eksportowanie `CArchive` operator wyodrębniania dla klas używających `DECLARE_SERIAL` i `IMPLEMENT_SERIAL` makra. Eksportuj operator archiwum przez nawiasy w deklaracjach klas (znajdujące się w. Plik H) z następującym kodem:  
  
```  
#undef AFX_API  
#define AFX_API AFX_EXT_CLASS  
 
<your class declarations here>  
 
#undef AFX_API  
#define AFX_API  
```  
  
### <a name="limitations-of-afxext"></a>Ograniczenia _AFXEXT  
 Można użyć _**AFXEXT** symbol wstępne procesora tak długo, jak nie ma wiele warstw biblioteki DLL rozszerzeń MFC z biblioteki DLL rozszerzenia MFC. Jeśli masz rozszerzenia MFC dll, które wywołania lub pochodzić od klasy własne rozszerzenia MFC dll, które następnie pochodzi od klasy MFC, należy użyć symbol preprocesora, aby uniknąć niejednoznaczności.  
  
 Problem jest tym w Win32, musisz jawnie zadeklarować wszystkie dane jako **__declspec(dllexport)** w celu wyeksportowania z biblioteki DLL, i **__declspec(dllimport)** w celu zaimportowania z biblioteki DLL. Podczas definiowania `_AFXEXT`, nagłówki MFC, upewnij się, że **afx_ext_class —** jest poprawnie zdefiniowany.  
  
 Jeśli masz wiele warstw, jeden symbol takich jak **afx_ext_class —** nie wystarcza, ponieważ bibliotekę DLL rozszerzenia MFC mogą być eksportowanie nowe klasy, a także importowanie innych klas z inną bibliotekę DLL rozszerzenia MFC. Aby rozwiązać ten problem, Użyj specjalnych symbol preprocesora, który wskazuje, czy tworzysz DLL porównaniu z użyciem biblioteki DLL. Załóżmy na przykład dwie biblioteki DLL rozszerzenia MFC, A.DLL i B.DLL. Niektóre klasy A.H i B.H, każdy z nich wyeksportować odpowiednio. B.DLL korzysta z klas z A.DLL. Pliki nagłówkowe będzie wyglądać mniej więcej tak:  
  
```  
/* A.H */  
#ifdef A_IMPL  
 #define CLASS_DECL_A   __declspec(dllexport)  
#else  
 #define CLASS_DECL_A   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_A CExampleA : public CObject  
{ ... class definition ... };  
 
/* B.H */  
#ifdef B_IMPL  
 #define CLASS_DECL_B   __declspec(dllexport)  
#else  
 #define CLASS_DECL_B   __declspec(dllimport)  
#endif  
 
class CLASS_DECL_B CExampleB : public CExampleA  
{ ... class definition .. };  
```  
  
 Po utworzeniu A.DLL został skompilowany za **/D A_IMPL** i po utworzeniu B.DLL został skompilowany za **/D B_IMPL**. Przy użyciu osobnych symbole dla każdej biblioteki DLL, CExampleB są eksportowane i CExampleA jest importowany podczas kompilowania B.DLL. CExampleA jest wyeksportowany podczas kompilowania A.DLL i zaimportować, gdy jest używana przez B.DLL (lub innego klienta).  
  
 Tworzenie warstw tego typu nie można wykonać przy użyciu wbudowanych **afx_ext_class —** i `_AFXEXT` symboli preprocesora. Techniki opisane powyżej rozwiązuje ten problem w sposób nie w przeciwieństwie do mechanizmu MFC sam używa podczas kompilowania jego OLE, bazy danych i sieci MFC biblioteki DLL rozszerzeń.  
  
### <a name="not-exporting-the-entire-class"></a>Nie eksportowania całej klasy  
 Ponownie należy zwrócić szczególną uwagę, gdy nie są eksportowane całej klasy. Należy poprawnie wyeksportowane elementy potrzebne dane utworzone przez makr MFC. Można to zrobić przez ponowne definiowanie **AFX_DATA** makra użytkownika określonej klasy. Należy to zrobić z dowolnym momencie całej klasy nie są eksportowane.  
  
 Na przykład:  
  
```  
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
*//class definition   
 .  
 .  
 .  
};  
 
#undef AFX_DATA  
#define AFX_DATA  
```  
  
### <a name="dllmain"></a>DllMain  
 Poniżej znajduje się dokładnie kod, który należy umieścić w pliku głównym źródłem bibliotekę DLL rozszerzenia MFC. Pochodziły po zawiera standardowe. Należy pamiętać, że korzystając z kreatorami AppWizard do tworzenia plików początkowy dla biblioteki DLL rozszerzenia MFC, podaje `DllMain` dla Ciebie.  
  
```  
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
  
 Wywołanie `AfxInitExtensionModule` przechwytuje modułów środowiska uruchomieniowego klasy (`CRuntimeClass` struktury) oraz jego fabryk obiektu (`COleObjectFactory` obiektów) do użycia w przypadku nowszych **CDynLinkLibrary** tworzony jest obiekt. (Opcjonalnie) wywołanie `AfxTermExtensionModule` umożliwia MFC oczyszczania bibliotekę DLL rozszerzenia MFC podczas każdego procesu odłącza (które ma miejsce, gdy kończy proces lub gdy biblioteka DLL jest zwalnianie w **FreeLibrary** wywołać) z biblioteki DLL rozszerzenia MFC . Ponieważ większość rozszerzenia MFC DLL nie są ładowane dynamicznie (zazwyczaj są powiązane za pośrednictwem ich bibliotekami importowanymi), wywołanie `AfxTermExtensionModule` zazwyczaj nie jest konieczne.  
  
 Jeśli aplikacja ładuje i zwalnia dynamicznie biblioteki DLL rozszerzeń MFC, należy wywołać `AfxTermExtensionModule` zgodnie z powyższym. Należy również użyć `AfxLoadLibrary` i `AfxFreeLibrary` (zamiast funkcji Win32 **LoadLibrary** i **FreeLibrary**) Jeśli aplikacja korzysta z wielu wątków lub dynamicznie ładuje MFC Biblioteka DLL rozszerzenia. Przy użyciu `AfxLoadLibrary` i `AfxFreeLibrary` temu, że uruchamiania i wyłączania kod, który wykonuje się, gdy ładowany i zwalnianie biblioteki DLL rozszerzenia MFC nie doprowadzić do uszkodzenia globalne MFC.  
  
 Plik nagłówka AFXDLLX. H zawiera specjalne definicje struktury używane w bibliotekach DLL rozszerzenia MFC, np. definicji `AFX_EXTENSION_MODULE` i **CDynLinkLibrary**.  
  
 Globalny *extensionDLL* musi być zadeklarowana, jak pokazano. W przeciwieństwie do 16-bitową wersją MFC, można przydzielić pamięci i wywoływać funkcje MFC w tym czasie, ponieważ MFCxx.DLL jest w pełni zainicjowany w czasie Twojej `DllMain` jest wywoływana.  
  
### <a name="sharing-resources-and-classes"></a>Udostępnianie zasobów i klasy  
 Proste biblioteki DLL rozszerzenia MFC należy wyeksportować tylko kilka funkcji niskiej przepustowości do aplikacji klienckiej i nic więcej. Więcej bibliotek DLL intensywnie wykorzystujących interfejs użytkownika może chcieć wyeksportować klasy C++ i zasobów do aplikacji klienckiej.  
  
 Eksportowanie zasobów odbywa się za pośrednictwem listy zasobów. W każdej aplikacji znajduje się lista pojedynczo połączonego **CDynLinkLibrary** obiektów. Podczas wyszukiwania dla zasobu, większość standardowych implementacji MFC, które ładują zasobów przyjrzeć bieżącego modułu zasobów (`AfxGetResourceHandle`) i nie można odnaleźć przeszukiwania w przypadku listę **CDynLinkLibrary** obiektów próby załadowania żądany zasób.  
  
 Dynamiczne tworzenie obiektów C++ otrzymuje nazwę klasy C++ jest podobne. Mechanizm deserializacji obiektu MFC musi mieć wszystkie `CRuntimeClass` obiektów zarejestrowana, dzięki czemu można go odtworzyć za dynamiczne tworzenie obiektu C++ wymaganego typu co wcześniej była przechowywana w oparciu.  
  
 Jeśli chcesz, aby aplikacja kliencka używać klas w bibliotekę DLL rozszerzenia MFC, które są `DECLARE_SERIAL`, a następnie należy wyeksportować z klasy mają być widoczne dla aplikacji klienckiej. To również zostanie przeprowadzony przez krótki **CDynLinkLibrary** listy.  
  
 W przypadku przykładowej pojęcia zaawansowane MFC [DLLHUSK](../visual-cpp-samples.md), listy wygląda mniej więcej tak:  
  
```  
head ->   DLLHUSK.EXE   - or -   DLLHUSK.EXE  
 |      |  
    TESTDLL2.DLL TESTDLL2.DLL  
 |      |  
    TESTDLL1.DLL TESTDLL1.DLL  
 |      |  
 |      |  
    MFC90D.DLL MFC90.DLL  
```  
  
 MFCxx.DLL jest zazwyczaj ostatnie na liście klas i zasobów. MFCxx.DLL zawiera wszystkie standardowe zasoby MFC, w tym monitu ciągów dla wszystkich identyfikatory poleceń standardowych. Umieszczenia go na końcu listy umożliwia biblioteki dll i aplikacja kliencka nie ma swoje własne kopie standardowe zasoby MFC, ale aby zależne od zasobów udostępnionych w MFCxx.DLL zamiast tego.  
  
 Scalanie zasobów i nazwy klas wszystkich bibliotek DLL w przestrzeni nazw aplikacja kliencka ma wadą, które należy zachować ostrożność, jakie identyfikatory lub nazwy, które można wybrać. Oczywiście funkcję można wyłączyć ten nie eksportując albo zasobów lub **CDynLinkLibrary** obiektu do aplikacji klienckiej. [DLLHUSK](../visual-cpp-samples.md) próbki zarządza przestrzeń nazw udostępnionych zasobów przy użyciu wielu plików nagłówka. Zobacz [35 Uwaga techniczna](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md) więcej porad na korzystanie z zasobów udostępnionych plików.  
  
### <a name="initializing-the-dll"></a>Inicjowanie biblioteki DLL  
 Jak wspomniano powyżej, zazwyczaj należy utworzyć **CDynLinkLibrary** obiekt, aby wyeksportować klasy i zasobów do aplikacji klienckiej. Należy określić punkt wejścia wyeksportowanej zainicjować biblioteki DLL. Minimalny zestaw jest to procedura void, który nie przyjmuje żadnych argumentów i nie zwraca żadnego, ale może być coś, co Ci się podoba.  
  
 Każdej aplikacji klienta, który chce korzystać z biblioteki DLL należy wywołać metodę ta procedura inicjowania, korzystając z tej metody. Może również przydzielić to **CDynLinkLibrary** obiektu w Twojej `DllMain` tylko po wywołaniu `AfxInitExtensionModule`.  
  
 Procedura inicjowania, należy utworzyć **CDynLinkLibrary** obiektu sterty bieżącej aplikacji, powiązaną klasą rozszerzenia MFC DLL informacji. Można to zrobić z następujących czynności:  
  
```  
extern "C" extern void WINAPI InitXxxDLL()  
{  
    new CDynLinkLibrary(extensionDLL);

}  
```  
  
 Nazwa procedury *InitXxxDLL* w tym przykładzie może być dowolną inną. Musi być `extern "C"`, ale wykonanie tak powoduje, że na liście eksportu łatwiejsze w obsłudze.  
  
> [!NOTE]
>  Jeśli korzystasz z biblioteki DLL rozszerzenia MFC ze standardowych bibliotek DLL MFC, należy wyeksportować tej funkcji inicjowania. Ta funkcja musi być wywołana ze standardowych biblioteki MFC DLL przed użyciem dowolnej klasy biblioteki DLL rozszerzenia MFC lub zasobów.  
  
### <a name="exporting-entries"></a>Eksportowanie wpisów  
 Prosty sposób, aby wyeksportować klas jest użycie **__declspec(dllimport)** i **__declspec(dllexport)** dla każdej klasy, a funkcja globalna do eksportowania. To ułatwia znacznie, ale jest mniej wydajne niż nazewnictwa każdego punktu wejścia (opisanych poniżej), ponieważ ma mniejszą kontrolę nad są eksportowane funkcje i nie można wyeksportować funkcji według liczby porządkowej. TESTDLL1 i TESTDLL2 Użyj tej metody, aby wyeksportować wpisów.  
  
 Bardziej wydajne (i metodę używaną przez MFCxx.DLL) nie jest eksportowane każdego wpisu ręcznie za pomocą nazw każdego wpisu w. DEF pliku. Ponieważ firma Microsoft są eksportowane selektywnego eksportu z naszych biblioteki DLL (to znaczy nie wszystko), możemy należy zdecydować, które interfejsy określonego możemy chcesz wyeksportować. Jest to trudne, ponieważ należy określić zniekształcone nazwy do konsolidatora w formularzu wpisów w pamięci. DEF pliku. Nie wyeksportować wszystkich klas C++, chyba że naprawdę musisz mieć łącza symbolicznego jego.  
  
 Jeśli wykonano C++ eksportowanie klas z. DEF pliku przed może zajść potrzeba Opracuj narzędzie można automatycznie wygenerować tej listy. Można to zrobić za pomocą łącza dwuetapowego procesu. Link biblioteki DLL jeden raz z żadnego eksportu, a następnie poczekanie konsolidator, aby wygenerować. Plik mapy. . Plik mapy może służyć do generowania listę funkcji, które powinny być eksportowane, dzięki z niektórych zmienianie rozmieszczenia, mogą być używane do generowania wpisy eksportu dla użytkownika. DEF pliku. Na liście eksportu MFCxx.DLL OLE i bibliotek DLL rozszerzeń MFC bazy danych, kilka tysięcy w polu numer został wygenerowany z takiego procesu (mimo że nie jest całkowicie automatyczne i wymaga niektórych ręcznie dostrajanie co raz za pewien czas).  
  
### <a name="cwinapp-vs-cdynlinklibrary"></a>Cwinapp — vs. CDynLinkLibrary  
 Biblioteka DLL rozszerzenia MFC nie ma `CWinApp`-pochodnych własnego obiektu; zamiast tego należy współpracować `CWinApp`-pochodnych obiektu aplikacji klienta. Oznacza to, aplikacja kliencka i tak dalej właścicielem pompa głównej wiadomości, pętli bezczynności.  
  
 Jeśli biblioteki DLL rozszerzenia MFC musi obsługiwać dodatkowe dane dla każdej aplikacji, może pochodzić z nową klasę **CDynLinkLibrary** i utwórz go w InitXxxDLL procedury opisano powyżej. Podczas uruchamiania, plik DLL, który można sprawdzić listę bieżącej aplikacji **CDynLinkLibrary** obiektów do znalezienia dla konkretnego rozszerzenia MFC DLL.  
  
### <a name="using-resources-in-your-dll-implementation"></a>Korzystanie z zasobów w implementacji biblioteki DLL  
 Jak wspomniano powyżej, ładowanie zasobów domyślne przeprowadzi listę **CDynLinkLibrary** obiektów wyszukiwanie pierwszy plik EXE lub DLL, która ma żądanego zasobu. Wszystkie interfejsy API MFC, jak również wszystkie używa wewnętrznego kodu `AfxFindResourceHandle` zawiera listę zasobów do wszystkich zasobów, niezależnie od tego, gdzie mogą znajdować się znaleźć.  
  
 Jeśli chcesz tylko załadować zasobów z określonego miejsca, przy użyciu interfejsów API `AfxGetResourceHandle` i `AfxSetResourceHandle` zapisać dojście stary i ustawić nowy uchwyt. Pamiętaj przywrócić stary dojście do zasobu przed zwróceniem do aplikacji klienckiej. Przykładowe TESTDLL2 korzysta z tej metody dla jawnego ładowania menu.  
  
 Przejście na liście ma wady jest wolniejsze i wymaga zarządzania zakresami identyfikator zasobu. Ma ona zaletą aplikacji klienta, który stanowi łącze do kilku bibliotek DLL rozszerzeń MFC można użyć dowolnego dostarczane do biblioteki DLL zasobu bez konieczności określania dojście wystąpienia biblioteki DLL. `AfxFindResourceHandle`Interfejs API służy do przejście listę zasobów do wyszukiwania dla danego dopasowania. Pobiera nazwę i typ zasobu, a zwraca dojście do zasobu którym najpierw zostało znalezione (lub wartość NULL).  
  
##  <a name="_mfcnotes_writing_an_application_that_uses_the_dll_version"></a>Pisanie aplikacji, która korzysta z wersji biblioteki DLL  
  
### <a name="application-requirements"></a>Wymagania dotyczące aplikacji  
 Aplikacja, która korzysta z udostępnionego wersji biblioteki MFC, należy wykonać kilka prostych reguł:  
  
-   Musi mieć `CWinApp` obiektu i wykonaj standardowe zasady dotyczące przekazywanie komunikatów.  
  
-   Muszą być skompilowane z zestawem flag wymagany kompilator (patrz poniżej).  
  
-   Go połączyć z bibliotekami importowanymi MFCxx. Ustawiając flagi kompilatora wymagane nagłówki MFC określają łączenia biblioteki, które aplikacji należy połączyć z.  
  
-   Aby uruchomić plik wykonywalny, MFCxx.DLL musi być w ścieżce lub w katalogu systemu Windows.  
  
### <a name="building-with-the-development-environment"></a>Kompilowanie z użyciem środowiska programowania  
 Jeśli używasz wewnętrznej pliku reguł programu make z większością standardowych wartościach domyślnych, można łatwo zmienić projekt do kompilacji wersja biblioteki DLL.  
  
 Następny krok przyjęto założenie, że masz prawidłowego działania aplikacji MFC związane z NAFXCWD. LIB (dla debugowania) i NAFXCW. LIB (dla sprzedaży detalicznej) i chcesz przekonwertować go do korzystania z udostępnionych wersji biblioteki MFC. Używasz środowiska Visual C++ i plik projektu wewnętrznej.  
  
1.  Na **projekty** menu, kliknij przycisk **właściwości**. W **ogólne** w obszarze **domyślne projektu**, ustawioną Microsoft Foundation Classes **Użyj MFC w bibliotece DLL udostępnionych** (MFCxx(d).dll).  
  
### <a name="building-with-nmake"></a>Kompilowanie z NMAKE  
 Jeśli jest używana funkcja zewnętrznego pliku reguł programu make Visual c++ lub używają NMAKE bezpośrednio, konieczne będzie edytować Twojego pliku reguł programu make do obsługi kompilatora i opcje konsolidatora  
  
 Kompilator flagi wymagane:  
  
 **/ / / D_AFXDLL MD**  
 **/ D_AFXDLL**  
  
 Standardowych nagłówków MFC należy ten symbol do zdefiniowania:  
  
 **/ / MD**  
 Aplikacja musi używać biblioteki DLL wersji biblioteki wykonawczej języka C  
  
 Wszystkie inne flagi kompilatora wykonaj domyślnych MFC (na przykład _DEBUG dla debugowania).  
  
 Edytuj listę bibliotek konsolidatora. Zmiana NAFXCWD. LIB do MFCxxD.LIB i zmień NAFXCW. LIB do MFCxx.LIB. Zastąp Biblioteka LIBC. LIB z MSVCRT. LIB. Podobnie jak w innych biblioteki MFC jest ważne, czy jest umieszczony MFCxxD.LIB **przed** żadnych bibliotek C runtime.  
  
 Opcjonalnie dodaj **/D_AFXDLL** do obu handlowych i debugowania — opcje kompilatora zasobów (który faktycznie kompiluje zasoby z **/R**). Dzięki temu końcowego pliku wykonywalnego mniejszych przez udostępnianie zasobów, które znajdują się w biblioteki DLL MFC.  
  
 Pełna ponowna kompilacja jest wymagany po wprowadzeniu tych zmian.  
  
### <a name="building-the-samples"></a>Tworzenie próbek  
 Większość MFC przykładowe programy mogą być tworzone z języka Visual C++ lub udostępnionego MAKEFILE NMAKE zgodnego z wiersza polecenia.  
  
 Aby dokonać konwersji żadnego z tych próbek do użycia MFCxx.DLL, można załadować. Klucz MAK pliku w Visual C++ i ustaw opcje projektu, zgodnie z powyższym opisem. Jeśli używasz kompilacji NMAKE, można określić "AFXDLL = 1" w NMAKE wiersz polecenia i który będzie tworzyć przykładowy kod za pomocą udostępnionej biblioteki MFC.  
  
 Pojęcia zaawansowane MFC próbki [DLLHUSK](../visual-cpp-samples.md) jest skompilowany jako wersja biblioteki DLL MFC. W tym przykładzie nie tylko ilustruje sposób tworzenia aplikacji związane z MFCxx.DLL, ale również dwie inne funkcje biblioteki MFC DLL opcja pakowania takich jak biblioteki DLL rozszerzenia MFC opisane w dalszej części tej uwagi techniczne.  
  
### <a name="packaging-notes"></a>Uwagi dotyczące tworzenia pakietów  
 Wersji detalicznej bibliotek DLL (MFCxx [U]. Biblioteki DLL) są za darmo do dystrybucji. Wersja do debugowania z bibliotek DLL nie są za darmo redistributable i powinien być używany tylko podczas opracowywania aplikacji.  
  
 Debugowanie bibliotek DLL są dostarczane z informacji o debugowaniu. Za pomocą debugera programu Visual C++, można śledzić wykonywania aplikacji, a także biblioteki DLL. Biblioteki DLL wersji (MFCxx [U]. Biblioteki DLL) nie zawiera informacji o debugowaniu.  
  
 Jeśli dostosować lub Odbuduj bibliotek DLL, następnie należy wywołać ich coś innego niż plik "MFCxx" SRC MFC MFCDLL. Klucz MAK opisano opcje kompilacji i zawiera logikę zmiana nazwy biblioteki DLL. Zmiana nazw plików jest konieczne, ponieważ te biblioteki DLL potencjalnie są współużytkowane przez wiele aplikacji MFC. O niestandardowej wersji biblioteki MFC DLL Zamień one zainstalowane w systemie mogą być dzielone innej aplikacji MFC za pomocą udostępnionej biblioteki DLL MFC.  
  
 Nie zaleca się ponowne tworzenie biblioteki DLL MFC.  
  
##  <a name="_mfcnotes_how_the_mfc30.dll_is_implemented"></a>Implementowania MFCxx.DLL  
 W poniższej sekcji opisano, jak jest implementowane biblioteki MFC DLL (MFCxx.DLL i MFCxxD.DLL). Tutaj również nie są istotne, jeśli wszystkie chcesz zrobić jest zrozumienie biblioteki MFC DLL za pomocą aplikacji. Tutaj nie są istotne dla zrozumienia, jak napisać bibliotekę DLL rozszerzenia MFC, ale opis tej implementacji mogą pomóc napisać własny biblioteki DLL.  
  
### <a name="implementation-overview"></a>Przegląd wdrożenia  
 Biblioteki MFC DLL to naprawdę szczególnych przypadkach biblioteki DLL rozszerzenia MFC, jak opisano powyżej. Ma bardzo dużej liczby eksportów dużej liczby klas. Istnieje kilka dodatkowych czynności, nie w bibliotece MFC DLL była bardziej specjalne niż regularne biblioteki DLL rozszerzenia MFC.  
  
### <a name="win32-does-most-of-the-work"></a>Większość pracy jest Win32  
 16-bitowej wersji biblioteki MFC potrzebne szereg technik specjalne, włącznie z danymi dla aplikacji w segmencie stosu segmentów specjalne utworzone przez niektóre kodu zestawu 80 x 86, kontekstów wyjątek na proces i innych technik. Win32 bezpośrednio obsługuje dane na proces w bibliotece DLL, który ma w większości przypadków. W większości przypadków MFCxx.DLL jest po prostu NAFXCW. LIB opakowane w bibliotece DLL. Podczas przeglądania w kodzie źródłowym MFC znajdują się bardzo mało _AFXDLL #ifdef, ponieważ istnieje bardzo niewiele szczególnych przypadkach, które należy wprowadzić. Szczególnych przypadkach, które są dostępne w szczególności na wypadek Win32 w systemie Windows 3.1 (znany także jako systemach Win32). Systemach Win32 nie nie pomocy technicznej na proces DLL danych bezpośrednio tak biblioteki MFC DLL należy użyć lokalny magazyn wątków (TLS) interfejsów API Win32, aby uzyskać dane lokalne procesu.  
  
### <a name="impact-on-library-sources-additional-files"></a>Wpływ na biblioteki źródeł, dodatkowe pliki  
 Wpływ **_AFXDLL** jest relatywnie wersja na normalne źródeł biblioteki klas MFC i nagłówków. Specjalna wersja pliku (AFXV_DLL. H), a także dodatkowe nagłówka pliku (AFXDLL_. H) uwzględnionych AFXWIN głównego. Nagłówek godz. AFXDLL_. H nagłówek zawiera **CDynLinkLibrary** klasy i inne szczegóły implementacji obu **_AFXDLL** aplikacji i bibliotek DLL rozszerzeń MFC. AFXDLLX. Nagłówek H podano do tworzenia biblioteki DLL rozszerzeń MFC (zobacz powyżej szczegółowe informacje).  
  
 Regularne źródeł do biblioteki MFC w MFC SRC ma dodatkowy kod warunkowe w obszarze **_AFXDLL** #ifdef. Plik źródłowy dodatkowe (DLLINIT. CPP) zawiera dodatkowy kod inicjowania biblioteki DLL i innych sklejki dla udostępnionych wersji biblioteki MFC.  
  
 Aby utworzyć udostępniony wersję MFC, znajdują się dodatkowe pliki. (Zobacz poniżej szczegółowe informacje na temat tworzenia biblioteki DLL).  
  
-   Dwa. DEF, pliki są używane do eksportowania biblioteki MFC DLL punkty wejścia do debugowania (MFCxxD.DEF) i wersji (MFCxx.DEF) biblioteki dll.  
  
-   . Plik RC (MFCDLL. RC) zawiera wszystkie standardowe zasoby MFC i zasób VERSIONINFO biblioteki dll.  
  
-   A. Plik CLW (MFCDLL. CLW) jest dostarczany, aby umożliwić przeglądanie MFC klasy przy użyciu ClassWizard. Uwaga: Ta funkcja nie jest dla wersja biblioteki DLL MFC.  
  
### <a name="memory-management"></a>Zarządzanie pamięcią  
 Aplikacji przy użyciu MFCxx.DLL używa wspólnego alokatora udostępniane przez MSVCRTxx.DLL, Wspólnej bibliotece DLL C runtime. Aplikacji, wszystkie biblioteki DLL rozszerzeń MFC i również biblioteki DLL MFC, same należy używać tego przydzielania pamięci współużytkowanej. Przy użyciu wspólnej bibliotece DLL alokacji pamięci, biblioteki DLL MFC można przydzielić pamięci, który zostanie później zwolniona przez aplikację lub na odwrót. Biblioteki DLL i aplikacji musi korzystać z tej samej przydzielania, nie powinny zastępować C++ globalne `operator new` lub `operator delete`. Te same zasady dotyczą reszty procedury alokacji pamięci środowiska wykonawczego języka C (takich jak `malloc`, `realloc`, **wolnego**i inne).  
  
### <a name="ordinals-and-class-declspecdllexport-and-dll-naming"></a>Porządkowe i __declspec(dllexport) klasy i nazwy biblioteki DLL  
 Nie używamy `class` **__declspec(dllexport)** funkcji kompilatora języka C++. Zamiast tego listę eksportu jest dołączany źródeł biblioteki klas (MFCxx.DEF i MFCxxD.DEF). Eksportowane są tylko te wybierz zestaw punktów wejścia (funkcji i danych). Inne symbole, takich jak funkcje prywatna implementacja MFC lub klasy nie zostaną wyeksportowane Eksportuje wszystkie te są wykonywane według liczby porządkowej bez nazwy ciągu w tabeli znajdują się lub niemających nazw.  
  
 Przy użyciu `class` **__declspec(dllexport)** może być realną alternatywę do tworzenia biblioteki DLL mniejsze, ale w przypadku dużych biblioteki DLL, takich jak MFC, domyślny mechanizm eksportu ma wydajność i pojemność limity.  
  
 Co to oznacza, że wszystkie jest czy możemy pakietu dużą ilość funkcje w wersji MFCxx.DLL, będzie on około 800 KB bez naruszania dużo wykonywania i szybkość ładowania. MFCxx.DLL byłby 100 KB większych ta metoda nie została używane. Ułatwia to też go można dodać dodatkowe punkty wejścia na końcu. Plik DEF umożliwia proste przechowywanie wersji bez obniżania wydajności szybkość i rozmiar eksportowania według liczby porządkowej. Wersja główna poprawki w bibliotece klas MFC zmieni nazwę biblioteki. Oznacza to, MFC30. Biblioteka DLL jest pakiet redystrybucyjny pliku DLL zawierającego wersji 3.0 Biblioteka klas MFC. Uaktualnienie tę bibliotekę DLL powiedzieć w hipotetyczny 3.1 MFC DLL będą miały postać MFC31. Biblioteki DLL zamiast tego. Ponownie należy zmodyfikować kod źródłowy MFC, aby utworzyć niestandardową wersję biblioteki MFC DLL, należy użyć, inną nazwę (i najlepiej bez "MFC" w nazwie).  
  
## <a name="see-also"></a>Zobacz też  
 [Uwagi techniczne według numerów](../mfc/technical-notes-by-number.md)   
 [Uwagi techniczne według kategorii](../mfc/technical-notes-by-category.md)

