---
title: 'Przewodnik przenoszenia: Narzędzie Spy modelu COM'
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: ec928768307a38cbb6ea00d985d60e6c2311b563
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449086"
---
# <a name="porting-guide-com-spy"></a>Przewodnik przenoszenia: Narzędzie Spy modelu COM

Ten temat jest drugi w serii artykułów pokazano proces uaktualniania starszej programu Visual Studio C++ projekty do najnowszej wersji programu Visual Studio. Przykładowy kod w tym temacie ostatnio został skompilowany przy użyciu programu Visual Studio 2005.

## <a name="comspy"></a>COMSpy

COMSpy to program, który monitoruje i rejestruje działanie obsługiwanych składników na maszynie. Obsługiwane składniki są składników modelu COM +, które są uruchamiane w systemie i mogą być używane przez komputery w tej samej sieci. Są one zarządzane przez funkcje usługi składowe w Panelu sterowania Windows.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Konwertowanie pliku projektu.
Plik projektu konwertuje łatwo i generuje raport z migracji. Istnieje kilka wpisów w raporcie, który NAS informują o problemach, które być może trzeba będzie dotyczyć. Oto jeden problem, który jest zgłaszany (Zwróć uwagę, że w tym temacie, komunikaty o błędach, czasami są skracane dla czytelności, na przykład aby usunąć pełnych ścieżek):

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

Jedną z częstych problemów w Uaktualnianie projektów jest to, że **Plik_wyjściowy konsolidatora** ustawienie w oknie dialogowym właściwości projektu może być konieczne do przeglądu. Dla projektów przed Visual Studio 2010 Plik_wyjściowy jest jedno ustawienie, który Kreator konwersji automatycznej ma problemy z, jeśli jest ustawiona na wartość niestandardową. W tym przypadku ścieżki dla plików wyjściowych zostały ustawione w folderze niestandardowych XP32_DEBUG. Aby dowiedzieć się więcej na temat tego błędu, możemy konsultacji [wpis w blogu](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx) związane z uaktualnienia projektu programu Visual Studio 2010, które zostało uaktualnienia z udziałem zmiana program vcbuild msbuild, istotną zmianę. Zgodnie z tych informacji, wartość domyślna **plik wyjściowy** ustawienie podczas tworzenia nowego projektu jest `$(OutDir)$(TargetName)$(TargetExt)`, ale to nie została ustawiona podczas konwersji, ponieważ nie jest możliwe w przypadku projektów przekonwertowany do sprawdzenia, czy wszystko jest poprawna. Jednak Załóżmy spróbuj umieścić w plik_wyjściowy i sprawdzić, czy działa.  Robi, więc możesz teraz przystąpić. Nie ma konkretnego powodu dotyczące korzystania z folderu danych wyjściowych niestandardowych, firma Microsoft zaleca użycie standardowego lokalizacji. W tym przypadku Wybraliśmy pozostaw lokalizację wyjściową jako niestandardowego typu w procesie przenoszenia i uaktualniania; `$(OutDir)` jest rozpoznawana jako folder XP32_DEBUG w **debugowania** konfiguracji i ReleaseU folder **wersji** konfiguracji.

### <a name="step-2-getting-it-to-build"></a>Krok 2. Wprowadzenie do kompilacji
Liczba błędy i ostrzeżenia kompilowania projektu przenieść, wystąpić.

`ComSpyCtl` nie kompilacji, jednak ze względu na następujący błąd kompilatora:

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

Błąd odwołania `Save` metody `IPersistStreamInitImpl` klasy w atlcom.h.

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

Problem polega na tym, że konwersji, która zaakceptowała starszej wersji kompilatora nie jest już prawidłowy. Aby można było zgodne ze standardem C++, kodu, który wcześniej był dozwolony nie jest już dozwolone. W tym przypadku nie jest bezpieczne przekazywanie wskaźnika niebędącego stałą do funkcji, która oczekuje wskaźnika elementu const.  To rozwiązanie ma na celu znalezienie deklaracji `IPersistStreamInit_Save` na `CComSpy` klasy, a następnie dodaj modyfikator const trzeciego parametru.

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

I podobne zmiany `IPersistStreamInit_Load`.

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

Następny błąd dotyczy rejestracji.

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

Nie potrzebujemy już to polecenie rejestracji po kompilacji. Zamiast tego, możemy po prostu usunąć niestandardowe polecenia kompilacji i określić w **konsolidatora** ustawienia, aby zarejestrować dane wyjściowe.

### <a name="dealing-with-warnings"></a>Radzenia sobie z ostrzeżeniami
Projekt zapewnia konsolidator następujące ostrzeżenie.

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

`/SAFESEH` — Opcja kompilatora nie jest użyteczny w trybie debugowania, która jest, gdy `/EDITANDCONTINUE` jest przydatne, więc poprawki w tym miejscu można wyłączyć `/SAFESEH` dla **debugowania** tylko konfiguracje. Aby to zrobić w oknie dialogowym właściwości, możemy otworzyć okno dialogowe właściwości dla projektu, który generuje ten błąd, a następnie wybrać opcję **konfiguracji** do **debugowania** (faktycznie **debugowania Unicode**), a następnie w polu **zaawansowanego konsolidatora** pozycję Resetuj **obraz ma bezpieczną obsługę wyjątków** właściwości **nie** (`/SAFESEH:NO`).

Kompilator ostrzega NAS, `PROP_ENTRY_EX` jest przestarzała. Nie jest bezpieczny i jest zalecana zastępuje `PROP_ENTRY_TYPE_EX`.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Możemy zmienić kod w ccomspy.h w związku z tym dodanie typów modelu COM, zgodnie z potrzebami.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Pojawiają się w dół do ostatniego kilka ostrzeżeń, które również są spowodowane przez bardziej rygorystyczne kontrole zgodności kompilatora:

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

Ostrzeżenie C4018 pochodzi z tego kodu:

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

Problem jest to, że `i` jest zadeklarowany jako `UINT` i `lCount` jest zadeklarowany jako **długie**, dlatego niezgodność ze znakiem/bez znaku. Jest wygodne, aby zmienić typ `lCount` do `UINT`, ponieważ pobiera ona swoją wartość od `IMtsEventInfo::get_Count`, typ, który używa **długie**i nie jest w kodzie użytkownika. Dlatego dodamy rzutowanie w kodzie. Rzutowania w stylu języka C jak w przypadku wartości liczbowych rzutowania, takich jak ta, ale **static_cast** jest zalecane stylu.

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

Tych ostrzeżeń są przypadki, w którym zmienna została zadeklarowana w funkcji, która ma parametr o tej samej nazwie, co prowadzi do potencjalnie mylące kodu. Naprawiliśmy, zmieniając nazwy zmiennych lokalnych.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testowanie i debugowanie
Firma Microsoft przetestowano aplikację najpierw z za pośrednictwem różnych menu i poleceń, a następnie zamknięcie aplikacji. Problem tylko zauważyć był asercji debugowania, od zamknięcia aplikacji. Problem pojawił się w destruktorze dla `CWindowImpl`, jako klasa bazowa `CSpyCon` obiektu, składnika COM z głównego aplikacji. Wystąpił błąd asercji w poniższym kodzie w atlwin.h.

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

`hWnd` Zwykle jest równa zero `WindowProc` funkcji, ale nie zostało to, że zamiast domyślnego `WindowProc`, niestandardowy program obsługi zostanie wywołana dla komunikatów Windows (WM_SYSCOMMAND), która umożliwia zamknięcie okna. Niestandardowe procedury obsługi zostało to ustawienie nie zostanie `hWnd` do zera. Przyjrzeć się podobny kod w MFC `CWnd` klasy, pokazuje, że kiedy niszczony jest oknem, `OnNcDestroy` jest wywołana i w MFC, dokumentacja informacją o tym, że podczas zastępowania `CWnd::OnNcDestroy`, base `NcDestroy` powinna być wywoływana, aby upewnić się, że po prawej stronie Oczyszczanie operacje są wykonywane, oddzielając uchwyt okna z poziomu okna, w tym lub innymi słowy, ustawianie `hWnd` do zera. Ta asercja mógł zostać wyzwolony w oryginalną wersję przykładu, ponieważ ten sam kod potwierdzenia znajdował się w starej wersji atlwin.h.

Aby przetestować działanie aplikacji, utworzyliśmy **obsługiwanych składników** przy użyciu szablonu projektu biblioteki ATL, wybrać dodanie obsługi modelu COM + w Kreatorze projektu ATL. Jeśli jeszcze nie znasz obsługiwanych składników przed, nie jest trudne ją utworzyć i Uzyskaj ją zarejestrowane i są dostępne w systemie lub sieci dla innych aplikacji do użycia. Aplikacja narzędzie Spy modelu COM jest przeznaczona do monitorowania aktywności obsługiwanych składników jako diagnostycznej.

Następnie możemy dodać klasę, wybrany obiekt ATL i określona nazwa obiektu jako `Dog`. Następnie w dog.h i dog.cpp dodaliśmy wdrożenia.

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

Następnie mamy skompilowane i rejestracji (należy uruchomić program Visual Studio jako Administrator) i aktywować go za pomocą **obsługiwanych składników** aplikacji w Panelu sterowania Windows. Firma Microsoft utworzony projekt C# Windows Forms, przeciągnięte przycisku z przybornika do formularza i który kliknął do obsługi zdarzeń kliknięcia. Dodano następujący kod, aby utworzyć wystąpienie `Dog` składnika.

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

To został uruchomiony bez problemów i za pomocą narzędzie Spy modelu COM pracę i skonfigurowany do monitorowania `Dog` składnika dużą ilość danych zostanie wyświetlona działania.

## <a name="see-also"></a>Zobacz także

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Następny przykład: Spy++](../porting/porting-guide-spy-increment.md)<br/>
[Poprzedni przykład: MFC Scribble](../porting/porting-guide-mfc-scribble.md)
