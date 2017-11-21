---
title: "Przewodnik przenoszenia: Narzędzie Spy modelu COM | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5e30d0664716df0f4cdf7d394d9c9a5fd7e8c798
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="porting-guide-com-spy"></a>Przewodnik przenoszenia: narzędzie Spy modelu COM
Ten temat jest drugi w serii artykułów, która ilustruje proces uaktualniania starsze projektów Visual C++ do najnowszej wersji programu Visual Studio. Przykładowy kod w tym temacie ostatnio został skompilowany z programu Visual Studio 2005.  
  
## <a name="comspy"></a>COMSpy  
 COMSpy to program, który monitoruje i rejestruje działanie serwisowanych składników na komputerze. Obsługiwane składniki są składniki modelu COM +, uruchom na komputerze, które mogą być używane przez komputery w tej samej sieci. Są one zarządzane przez funkcje usługi składowe w Panelu sterowania systemu Windows.  
  
### <a name="step-1-converting-the-project-file"></a>Krok 1. Konwertowanie pliku projektu.  
 Plik projektu konwertuje łatwo i tworzy raport migracji. Istnieje kilka wpisów w raporcie, który nas o tym poinformować o problemach, które może być konieczne radzenia sobie z. Oto jeden problem, który jest zgłaszany (należy pamiętać, że w tym temacie komunikaty o błędach są czasami skracane, tak aby zwiększyć czytelność, na przykład usunąć pełne ścieżki):  
  
```Output  
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).  
```  
  
 Jednym z częstych problemów Uaktualnianie projektów jest ustawienie OutputFile konsolidatora w oknie dialogowym właściwości projektu może być konieczne zrecenzowane. Dla projektów przed Visual Studio 2010 OutputFile to jeden ustawienie automatycznej konwersji Kreator ma problemy z, jeśli jest ustawiona na wartość niestandardowych. W takim przypadku ścieżki do plików wyjściowych zostały ustawione w folderze niestandardowe XP32_DEBUG. Aby dowiedzieć się więcej na temat tego błędu, możemy konsultacji [wpis w blogu](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) dotyczące uaktualniania projektu Visual C++ 2010 został uaktualnienia uczestniczący zmiany program vcbuild msbuild, znaczące zmiany. Zgodnie z tych informacji, wartością domyślną dla pliku wyjściowego ustawienie podczas tworzenia nowego projektu jest $(OutDir)$(TargetName)$(TargetExt), ale nie została ustawiona podczas konwersji, ponieważ nie jest możliwe w dla projektów przekonwertowanego sprawdzić, czy wszystko jest Popraw.  Jednak umożliwia spróbuj umieścić w plik_wyjściowy i sprawdzić, czy działa.  Tak, więc możesz teraz przystąpić. Jeśli nie ma żadnego określonego powodu dotyczące korzystania z folderu wyjściowego niestandardowe, zaleca się przy użyciu standardowej lokalizacji. W takim przypadku Wybraliśmy pozostaw lokalizacja danych wyjściowych jako niestandardowych podczas procesu przenoszenia i uaktualniania; Rozpoznaje $(OutDir) w folderze XP32_DEBUG w konfiguracji debugowania i folderu ReleaseU do konfiguracji wydania.  
  
### <a name="step-2-getting-it-to-build"></a>Krok 2. Wprowadzenie do kompilacji  
 Liczba błędów i ostrzeżeń kompilowania przenieść projektu, wystąpić.  
  
 ComSpyCtl nie kompilacji, ale z powodu tego błędu kompilatora:  
  
```Output  
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled  
```  
  
 Błąd odwołuje się do metody Zapisz w klasie IPersistStreamInitImpl w atlcom.h.  
  
```cpp  
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)  
{  
     T* pT = static_cast<T*>(this);  
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));  
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());  
}  
```  
  
 Problem polega na starszą wersję kompilatora akceptowane konwersji jest już nieprawidłowy. Aby można było zgodne ze standardem C++, niektóre kod, który wcześniej zezwolono nie jest dozwolony. W takim przypadku nie jest bezpieczne wskaźnikiem do funkcji, która oczekuje wskaźnika const z systemem innym niż stała.  Rozwiązanie jest odnaleźć deklaracji klasy CComSpy IPersistStreamInit_Save i Dodaj modyfikator const trzeciego parametru.  
  
```cpp  
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)  
  
```  
  
 I podobne zmiany IPersistStreamInit_Load.  
  
```cpp  
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);  
```  
  
 Następny błąd podchodzi do rejestracji.  
  
```Output  
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.  
```  
  
 Nie musisz już to polecenie rejestracji po kompilacji. Zamiast tego możemy po prostu usuń polecenia niestandardowych kompilacji i określonymi w ustawieniach konsolidatora do rejestrowania danych wyjściowych.  
  
### <a name="dealing-with-warnings"></a>Do czynienia z ostrzeżeniami  
 Projekt zapewnia następujące konsolidator ostrzeżenie.  
  
```Output  
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification  
```  
  
 Opcja/SAFESEH — opcja kompilatora nie jest przydatne w trybie debugowania, czyli gdy/editandcontinue jest przydatne, dlatego w tym miejscu będzie można wyłączyć tylko konfiguracje Debug opcja/SAFESEH. Aby to zrobić w oknie dialogowym właściwości, możemy otworzyć okno dialogowe właściwości projektu, który spowoduje utworzenie tego błędu i firma Microsoft najpierw ustawienia konfiguracji debugowania (faktycznie debugowania Unicode), a następnie w sekcji Zaawansowane konsolidatora zresetować właściwość obraz ma bezpieczną obsługę wyjątków nie (/ SAFESEH:NO).  
  
 Kompilator ostrzega nam czy PROP_ENTRY_EX jest przestarzały. Nie jest bezpieczna i zalecana substitute jest PROP_ENTRY_TYPE_EX.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 Możemy zmienić kod w ccomspy.h w związku z tym dodawanie typów COM zależnie od potrzeb.  
  
```cpp  
BEGIN_PROPERTY_MAP(CComSpy)  
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)  
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)  
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)  
     PROP_PAGE(CLSID_StockFontPage)  
END_PROPERTY_MAP()  
```  
  
 Konfigurujemy wszystko w dół do ostatniego kilka ostrzeżeń, które także spowodowane ściślejsze sprawdza zgodność kompilatora:  
  
```Output  
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'  
```  
  
 Ostrzeżenie C4018 pochodzi z tego kodu:  
  
```cpp  
for (i=0;i<lCount;i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 Problem jest i jest zadeklarowany jako UINT oraz lCount zadeklarowano tak długo, dlatego niezgodność podpisany unsigned. Jest niedogodne zmienić typ lCount UINT, ponieważ pobiera ona swoją wartość z IMtsEventInfo::get_Count, która używa typu long i nie jest w kodzie użytkownika. Sposób dodania rzutowanie do kodu. Rzutowania w stylu języka C sposób jak numeryczny rzutowania, takich jak ta, ale static_cast jest zalecane stylu.  
  
```cpp  
for (i=0;i<static_cast<UINT>(lCount);i++)  
    CoTaskMemFree(pKeys[i]);  
```  
  
 Tych ostrzeżeń są przypadków, gdy zmienna została zadeklarowana w funkcji, która ma parametr o tej samej nazwie, co może prowadzić do potencjalnie skomplikowana kodu. Usunięto który zmieniając nazwy zmiennych lokalnych.  
  
### <a name="step-3-testing-and-debugging"></a>Krok 3. Testowanie i debugowanie  
 Przetestowaliśmy aplikacji z najpierw uruchomiony za pośrednictwem różnych menu i poleceń, a następnie zamknięcie aplikacji. Problem tylko zauważyć został potwierdzenia debugowania, od zamknięcia aplikacji. Problem pojawił się w destruktor dla CWindowImpl, klasę podstawową obiektu CSpyCon główny składnik modelu COM aplikacji. Wystąpił błąd potwierdzenia w poniższym kodzie w atlwin.h.  
  
```cpp  
virtual ~CWindowImplRoot()  
{  
     #ifdef _DEBUG  
     if(m_hWnd != NULL)// should be cleared in WindowProc  
     {  
          ATLTRACE(atlTraceWindowing, 0, _T("ERROR - Object deleted before window was destroyed\n"));  
          ATLASSERT(FALSE);  
     }  
     #endif //_DEBUG  
}  
```  
  
 HWnd zwykle jest ustawione na zero w funkcji WindowProc, ale które nie zostały się zdarzyć, zamiast domyślnej WindowProc niestandardowy program obsługi jest wywoływana dla komunikatów systemu Windows (WM_SYSCOMMAND), który zamyka okno. Niestandardowy program obsługi nie została ustawienie hWnd na zero. Obejrzyj podobny kod w klasie CWnd MFC, pokazuje, że gdy okno jest niszczony, OnNcDestroy jest wywoływana i w MFC, dokumentacji informacją o tym, że w przypadku przesłaniania CWnd::OnNcDestroy, NcDestroy podstawowej należy wywołać do upewnij się, że prawo czyszczenia operacje są wykonywane, łącznie z oddzielającym uchwytu okna w oknie lub innymi słowy, ustawienie hWnd na zero. To potwierdzenie może zostało wyzwolone w oryginalnej wersji próbki, jak również od tego samego kodu potwierdzenia był obecny w starej wersji atlwin.h.  
  
 Aby przetestować funkcje aplikacji, utworzyliśmy składnik obsługiwane za pomocą szablonu projektu ATL, wybrana opcja dodanie obsługi modelu COM + w Kreatorze projektu ATL. Jeśli nie pracowano z obsługiwanych składników przed nie jest trudne do utworzyć i uzyskać, zarejestrowane i są dostępne w systemie lub w sieci dla innych aplikacji do użycia. Narzędzie Spy modelu COM aplikacji zaprojektowano w celu monitorowania aktywności serwisowanych składników jako pomoc diagnostyczna.  
  
 Następnie możemy dodać klasę wybrany obiekt ATL i określona nazwa obiektu jako Dog. Następnie w dog.h i dog.cpp dodano implementacji.  
  
```cpp  
STDMETHODIMP CDog::Wag(LONG* lDuration)  
{  
    // TODO: Add your implementation code here  
    *lDuration = 100l;  
    return S_OK;  
}  
```  
  
 Następnie firma Microsoft wbudowane i zarejestrować go (należy uruchomić program Visual Studio jako Administrator) i aktywować przy użyciu aplikacji obsługiwanych składników w Panelu sterowania systemu Windows. Firma Microsoft utworzony projekt formularzy systemu Windows w języku C#, przeciągnąć przycisk w formularzu z przybornika i podwójnie który do obsługi zdarzenia kliknięcia. Dodano następujący kod do utworzenia wystąpienia składnika Dog.  
  
```cpp  
private void button1_Click(object sender, EventArgs e)  
{  
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();  
    dog1.Wag();  
}  
```  
  
 To został uruchomiony bez problemów oraz narzędzie Spy modelu COM w górę i uruchomiona i skonfigurowana do monitorowania składnika Dog duże ilości danych wyświetleniu działania.  
  
## <a name="see-also"></a>Zobacz też  
 [Przenoszenie i uaktualnianie: przykłady i analizy przypadków:](../porting/porting-and-upgrading-examples-and-case-studies.md)   
 [Przykład dalej: Narzędzie Spy ++](../porting/porting-guide-spy-increment.md)   
 [Poprzednim przykładzie: Aplikacja Scribble MFC](../porting/porting-guide-mfc-scribble.md)