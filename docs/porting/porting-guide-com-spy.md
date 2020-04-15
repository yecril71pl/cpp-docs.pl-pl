---
title: 'Przewodnik przenoszenia: narzędzie Spy modelu COM'
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: f4fece07b9ea4541d8bf21dd81fd659b44f39718
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368458"
---
# <a name="porting-guide-com-spy"></a>Przewodnik przenoszenia: narzędzie Spy modelu COM

Ten temat jest drugim z serii artykułów, który pokazuje proces uaktualniania starszych projektów Visual Studio C++ do najnowszej wersji programu Visual Studio. Przykładowy kod w tym temacie został ostatnio skompilowany z programem Visual Studio 2005.

## <a name="comspy"></a>COMSpy (włask.)

COMSpy to program, który monitoruje i rejestruje aktywność obsługiwanych składników na komputerze. Obsługiwane składniki to składniki COM+, które działają w systemie i mogą być używane przez komputery w tej samej sieci. Są one zarządzane przez funkcje usług składowych w Panelu sterowania systemu Windows.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Konwertowanie pliku projektu

Plik projektu można łatwo konwertować i tworzy raport migracji. W raporcie znajduje się kilka wpisów, które informują nas o problemach, z którymi być może musimy się uporać. Oto jeden z zgłaszanych problemów (należy pamiętać, że w tym temacie komunikaty o błędach są czasami skracane w celu odczytu, na przykład w celu usunięcia pełnych ścieżek):

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

Jednym z częstych problemów w uaktualnianiu projektów jest to, że ustawienie **Danych wyjściowych konsoli w** oknie dialogowym właściwości projektu może wymagać przejrzenia. W przypadku projektów przed programem Visual Studio 2010 plik output jest jednym z ustawień, z którymi kreator konwersji automatycznej ma problemy, jeśli jest ustawiony na wartość niestandardową. W takim przypadku ścieżki dla plików wyjściowych zostały ustawione na niestandardowy folder, XP32_DEBUG. Aby dowiedzieć się więcej o tym błędzie, skonsultowaliśmy się z [wpisem w blogu](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) związanym z uaktualnieniem projektu programu Visual Studio 2010, które było uaktualnieniem, które obejmowało zmianę z vcbuild na msbuild, istotną zmianę. Zgodnie z tymi informacjami domyślną wartością ustawienia **Plik wyjściowy** podczas tworzenia nowego projektu jest , ale nie jest `$(OutDir)$(TargetName)$(TargetExt)`ustawiona podczas konwersji, ponieważ nie jest możliwe, aby przekonwertowane projekty sprawdzały, czy wszystko jest poprawne. Spróbujmy jednak wprowadzić to dla pliku output i sprawdzić, czy to działa.  Tak, więc możemy iść dalej. Jeśli nie ma żadnego konkretnego powodu używania niestandardowego folderu wyjściowego, zaleca się użycie lokalizacji standardowej. W takim przypadku zdecydowaliśmy się opuścić lokalizację wyjściową jako niestandardową podczas procesu przenoszenia i uaktualniania; `$(OutDir)` jest rozpoznawany w folderze XP32_DEBUG w konfiguracji **debugowania** i w folderze ReleaseU dla konfiguracji **wydania.**

### <a name="step-2-getting-it-to-build"></a>Krok 2. Tworzenie go do budowy

Podczas tworzenia projektu przeniesionego pojawia się szereg błędów i ostrzeżeń.

`ComSpyCtl`nie skompilować jednak z powodu tego błędu kompilatora:

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

Błąd odwołuje się `Save` do `IPersistStreamInitImpl` metody w klasie w atlcom.h.

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

Problem polega na tym, że konwersja, że starsza wersja kompilatora akceptowane nie jest już prawidłowa. Aby zapewnić zgodność ze standardem C++, niektóre kody, które wcześniej były dozwolone, nie są już dozwolone. W takim przypadku nie jest bezpieczne, aby przekazać wskaźnik non-const do funkcji, która oczekuje wskaźnika const.  Rozwiązaniem jest znalezienie deklaracji `IPersistStreamInit_Save` na `CComSpy` klasy i dodać const modyfikator do trzeciego parametru.

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

I podobna `IPersistStreamInit_Load`zmiana do .

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

Następny błąd dotyczy rejestracji.

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

Nie potrzebujemy już tego polecenia rejestracji po kompilacji. Zamiast tego po prostu usunąć polecenie kompilacji niestandardowej i określić w ustawieniach **konsolidatora,** aby zarejestrować dane wyjściowe.

### <a name="dealing-with-warnings"></a>Radzenie sobie z ostrzeżeniami

Projekt generuje następujące ostrzeżenie konsolidatora.

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

Opcja `/SAFESEH` kompilatora nie jest przydatna w `/EDITANDCONTINUE` trybie debugowania, który `/SAFESEH` jest przydatny, więc poprawka w tym miejscu jest, aby wyłączyć tylko dla konfiguracji **debugowania.** Aby to zrobić w oknie dialogowym właściwości, otwieramy okno dialogowe właściwości dla projektu, który generuje ten błąd, a najpierw ustawiamy **konfigurację** na **Debug** (faktycznie **Debug Unicode),** a następnie w sekcji **Zaawansowane konsolidator** resetuj właściwość **Image Has Safe Exception Handlers** na **Nie** (`/SAFESEH:NO`).

Kompilator ostrzega `PROP_ENTRY_EX` nas, że jest przestarzałe. To nie jest bezpieczne, a `PROP_ENTRY_TYPE_EX`zalecanym substytutem jest .

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Odpowiednio zmieniamy kod w ccomspy.h, dodając odpowiednie typy COM.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Zbliżamy się do kilku ostatnich ostrzeżeń, które są również spowodowane bardziej rygorystycznymi kontrolami zgodności kompilatora:

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

Ostrzeżenie C4018 pochodzi z tego kodu:

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

Problem polega `i` na tym, że jest zadeklarowany jako `UINT` i `lCount` jest zadeklarowany tak **długo,** stąd podpisane/niepodpisane niezgodność. Byłoby niewygodne, aby zmienić typ `lCount` na `UINT`, ponieważ pobiera `IMtsEventInfo::get_Count`jego wartość z , który używa typu **długo**i nie jest w kodzie użytkownika. Więc dodajemy oddanych do kodu. Rzutowania w stylu C zrobi dla oddanych numerycznych, takich jak ten, ale **static_cast** jest zalecany styl.

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

Te ostrzeżenia są przypadki, gdy zmienna została zadeklarowana w funkcji, która ma parametr o tej samej nazwie, co prowadzi do potencjalnie mylące kodu. Naprawiliśmy to, zmieniając nazwy zmiennych lokalnych.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testowanie i debugowanie

Przetestowaliśmy aplikację najpierw uruchamiając różne menu i polecenia, a następnie zamykając aplikację. Jedynym odnotowanym problemem było potwierdzenie debugowania po zamknięciu aplikacji. Problem pojawił się w destruktorze dla `CWindowImpl` `CSpyCon` , klasy podstawowej obiektu, głównego składnika COM aplikacji. Wystąpił błąd potwierdzenia w poniższym kodzie w pliku atlwin.h.

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

Jest `hWnd` zwykle ustawiona na `WindowProc` zero w funkcji, ale tak się nie `WindowProc`stało, ponieważ zamiast domyślnego , niestandardowy program obsługi jest wywoływana dla wiadomości systemu Windows (WM_SYSCOMMAND), który zamyka okno. Program obsługi niestandardowej `hWnd` nie ustawiał wartości zero. Spojrzenie na podobny kod w `CWnd` klasie MFC, pokazuje, że gdy `OnNcDestroy` okno jest niszczone, jest wywoływana, a `CWnd::OnNcDestroy`w `NcDestroy` MFC, dokumentacja informuje, że podczas zastępowania , podstawy powinny być wywoływane, aby upewnić się, że występują operacje oczyszczania prawo, w tym oddzielenie dojścia okna z okna lub innymi słowy, ustawienie `hWnd` do zera. To stwierdzenie może być wyzwalane w oryginalnej wersji próbki, jak również, ponieważ ten sam kod potwierdzenia był obecny w starej wersji atlwin.h.

Aby przetestować funkcjonalność aplikacji, utworzyliśmy **serviced component** przy użyciu szablonu projektu ATL, zdecydowaliśmy się dodać obsługę COM+ w kreatorze projektu ATL. Jeśli wcześniej nie pracowałeś z obsługiwanymi składnikami, nie jest trudno je utworzyć i uzyskać jeden zarejestrowany i dostępny w systemie lub sieci, aby inne aplikacje można było używać. Aplikacja COM Spy jest przeznaczona do monitorowania aktywności obsługiwanych komponentów jako pomocy diagnostycznej.

Następnie dodaliśmy klasę, wybraliśmy obiekt ATL i `Dog`określiliśmy nazwę obiektu jako . Następnie w dog.h i dog.cpp dodaliśmy implementację.

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

Następnie stworzyliśmy go i zarejestrowaliśmy (musisz uruchomić program Visual Studio jako administrator) i aktywowaliśmy go za pomocą aplikacji **Serviced Component** w Panelu sterowania systemu Windows. Utworzyliśmy projekt formularzy windows systemu Windows w języku C#, przeciągnęliśmy przycisk do formularza z przybornika i kliknięliśmy go dwukrotnie, aby program obsługi zdarzeń kliknięć. Dodaliśmy następujący kod do wystąpienia `Dog` składnika.

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

To działało bez problemów, a z COM Spy `Dog` i działa i skonfigurowany do monitorowania składnika, wiele danych pojawia się pokazano aktywność.

## <a name="see-also"></a>Zobacz też

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Następny przykład: Szpieg++](../porting/porting-guide-spy-increment.md)<br/>
[Poprzedni przykład: Bazgroły MFC](../porting/porting-guide-mfc-scribble.md)
