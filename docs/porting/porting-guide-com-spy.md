---
title: 'Przewodnik przenoszenia: narzędzie Spy modelu COM'
ms.date: 11/04/2016
ms.assetid: 24aa0d52-4014-4acb-8052-f4e2e4bbc3bb
ms.openlocfilehash: c21049a2faa8bb34ecd1ba75a5beda1db119f0fc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230288"
---
# <a name="porting-guide-com-spy"></a>Przewodnik przenoszenia: narzędzie Spy modelu COM

Ten temat jest drugą częścią serii artykułów demonstrujących proces uaktualniania starszych projektów programu Visual Studio C++ do najnowszej wersji programu Visual Studio. Przykładowy kod w tym temacie został ostatnio skompilowany przy użyciu programu Visual Studio 2005.

## <a name="comspy"></a>COMSpy

COMSpy to program, który monitoruje i rejestruje aktywność składników usługi na komputerze. Składniki usługi są składnikami COM+, które działają w systemie i mogą być używane przez komputery w tej samej sieci. Są one zarządzane przez funkcję usługi składowe w panelu sterowania systemu Windows.

### <a name="step-1-converting-the-project-file"></a>Krok 1. Konwertowanie pliku projektu

Plik projektu jest łatwo konwertowany i tworzy raport migracji. Raport zawiera kilka wpisów informujących o problemach, z którymi może być konieczna transakcja. Oto jeden zgłoszony problem (należy zauważyć, że w tym temacie komunikaty o błędach są czasami skracane pod kątem czytelności, na przykład w celu usunięcia pełnych ścieżek):

```Output
ComSpyAudit\ComSpyAudit.vcproj: MSB8012: $(TargetPath) ('C:\Users\UserName\Desktop\spy\spy\ComSpyAudit\.\XP32_DEBUG\ComSpyAudit.dll') does not match the Librarian's OutputFile property value '.\XP32_DEBUG\ComSpyAudit.dll' ('C:\Users\UserName\Desktop\spy\spy\XP32_DEBUG\ComSpyAudit.dll') in project configuration 'Unicode Debug|Win32'. This may cause your project to build incorrectly. To correct this, please make sure that $(TargetPath) property value matches the value specified in %(Lib.OutputFile).
```

Jednym z częstych problemów w uaktualnianiu projektów jest to, że w oknie dialogowym właściwości projektu może być konieczne zweryfikowanie ustawienia **konsolidatora** . W przypadku projektów przed programem Visual Studio 2010, plik Plik_wyjściowy ma jedno ustawienie, którego Kreator konwersji automatycznej ma problemy z, jeśli jest ustawiona na wartość niestandardową. W takim przypadku ścieżki dla plików wyjściowych zostały ustawione na folder niestandardowy, XP32_DEBUG. Aby dowiedzieć się więcej na temat tego błędu, zapoznaj się z [wpisem w blogu](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/) związanym z uaktualnieniem projektu programu Visual Studio 2010, które było uaktualnieniem, które dotyczyło zmiany z vcbuild na MSBuild, istotną zmianą. Zgodnie z tymi informacjami wartość domyślna dla ustawienia **pliku wyjściowego** podczas tworzenia nowego projektu to `$(OutDir)$(TargetName)$(TargetExt)` , ale nie jest ona ustawiana podczas konwersji, ponieważ nie jest to możliwe w przypadku przekonwertowanych projektów, aby sprawdzić, czy wszystkie elementy są poprawne. Wypróbujmy jednak tę opcję w przypadku elementu Plik_wyjściowy i sprawdź, czy działa.  Robi to, więc możemy przejść do. Jeśli nie ma konkretnej przyczyny używania niestandardowego folderu wyjściowego, zalecamy użycie standardowej lokalizacji. W takim przypadku wybieramy lokalizację wyjściową jako niestandardową podczas procesu przenoszenia i uaktualniania. jest `$(OutDir)` rozpoznawany jako folder XP32_DEBUG w konfiguracji **debugowania** i w folderze ReleaseU dla konfiguracji **wydania** .

### <a name="step-2-getting-it-to-build"></a>Krok 2. Trwa przygotowywanie do kompilacji

Podczas kompilowania projektu portowego występuje wiele błędów i ostrzeżeń.

`ComSpyCtl`nie kompiluje się, chociaż z powodu błędu kompilatora:

```Output
atlcom.h(611): error C2664: 'HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM,BOOL,ATL::ATL_PROPMAP_ENTRY *)': cannot convert argument 3 from 'const ATL::ATL_PROPMAP_ENTRY *' to 'ATL::ATL_PROPMAP_ENTRY *'atlcom.h(611): note: Conversion loses qualifiersatlcom.h(608): note: while compiling class template member function 'HRESULT ATL::IPersistStreamInitImpl<CComSpy>::Save(LPSTREAM,BOOL)'\spy\spy\comspyctl\ccomspy.h(28): note: see reference to class template instantiation 'ATL::IPersistStreamInitImpl<CComSpy>' being compiled
```

Błąd odwołuje się do `Save` metody `IPersistStreamInitImpl` klasy w atlcom. h.

```cpp
STDMETHOD(Save)(_Inout_ LPSTREAM pStm, _In_ BOOL fClearDirty)
{
     T* pT = static_cast<T*>(this);
     ATLTRACE(atlTraceCOM, 2, _T("IPersistStreamInitImpl::Save\n"));
     return pT->IPersistStreamInit_Save(pStm, fClearDirty, T::GetPropertyMap());
}
```

Problem polega na tym, że konwersja, która została zaakceptowana przez starszą wersję kompilatora, nie jest już prawidłowa. Aby zapewnić zgodność ze standardem C++, kod, który wcześniej był dozwolony, nie jest już dozwolony. W tym przypadku nie jest bezpieczne przekazywanie wskaźnika niestałego do funkcji, która oczekuje wskaźnika const.  Rozwiązaniem jest znalezienie deklaracji `IPersistStreamInit_Save` `CComSpy` klasy i dodanie modyfikatora const do trzeciego parametru.

```cpp
HRESULT CComSpy::IPersistStreamInit_Save(LPSTREAM pStm, BOOL /* fClearDirty */, const ATL_PROPMAP_ENTRY* pMap)
```

I podobna zmiana do `IPersistStreamInit_Load` .

```cpp
HRESULT IPersistStreamInit_Load(LPSTREAM pStm, const ATL_PROPMAP_ENTRY* pMap);
```

Następny błąd dotyczy rejestracji.

```Output
error MSB3073: The command "regsvr32 /s /c "C:\Users\username\Desktop\spy\spy\ComSpyCtl\.\XP32_DEBUG\ComSpyCtl.lib"error MSB3073: echo regsvr32 exec. time > ".\XP32_DEBUG\regsvr32.trg"error MSB3073:error MSB3073: :VCEnd" exited with code 3.
```

To polecenie rejestracji po kompilacji nie jest już potrzebne. Zamiast tego po prostu usuniemy niestandardowe polecenie kompilacji i określisz w ustawieniach **konsolidatora** , aby zarejestrować dane wyjściowe.

### <a name="dealing-with-warnings"></a>Rozwiązywanie problemów z ostrzeżeniami

Projekt generuje następujące ostrzeżenie konsolidatora.

```Output
warning LNK4075: ignoring '/EDITANDCONTINUE' due to '/SAFESEH' specification
```

`/SAFESEH`Opcja kompilatora nie jest przydatna w trybie debugowania, co jest `/EDITANDCONTINUE` przydatne, więc poprawkę należy wyłączyć `/SAFESEH` tylko dla konfiguracji **debugowania** . Aby to zrobić w oknie dialogowym właściwości, otwieramy okno dialogowe właściwości dla projektu, który generuje ten błąd i najpierw ustawimy **konfigurację** na **Debuguj** (faktycznie **Debuguj kod Unicode**), a następnie w sekcji **Zaawansowane ustawienia konsolidatora** **obraz ma bezpieczną obsługę wyjątków** dla właściwości **nie** ( `/SAFESEH:NO` ).

Kompilator ostrzega nas, że `PROP_ENTRY_EX` jest przestarzały. Nie jest to bezpieczne i zaleca się podstawianie `PROP_ENTRY_TYPE_EX` .

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_ENTRY_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Zmienimy kod w CComSpy. h odpowiednio dodając odpowiednie typy COM.

```cpp
BEGIN_PROPERTY_MAP(CComSpy)
     PROP_ENTRY_TYPE_EX( "LogFile", DISPID_LOGFILE, CLSID_ComSpyPropPage, IID_IComSpy, VT_BSTR)
     PROP_ENTRY_TYPE_EX( "ShowGridLines", DISPID_GRIDLINES, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "Audit", DISPID_AUDIT, CLSID_ComSpyPropPage, IID_IComSpy, VT_BOOL)
     PROP_ENTRY_TYPE_EX( "ColWidth", DISPID_COLWIDTH, CLSID_ComSpyPropPage, IID_IComSpy, VT_UINT)
     PROP_PAGE(CLSID_StockFontPage)
END_PROPERTY_MAP()
```

Zaczynamy od najnowszych ostrzeżeń, które są również spowodowane bardziej rygorystycznymi sprawdzeniami zgodności kompilatora:

```Output
\spy\comspyctl\usersub.h(70): warning C4457: declaration of 'var' hides function parameter\spy\comspyctl\usersub.h(48): note: see declaration of 'var'\spy\comspyctl\usersub.h(94): warning C4018: '<': signed/unsigned mismatch  ComSpy.cpp\spy\comspyctl\comspy.cpp(186): warning C4457: declaration of 'bHandled' hides function parameter\spy\spy\comspyctl\comspy.cpp(177): note: see declaration of 'bHandled'
```

C4018 ostrzegawczy pochodzi z tego kodu:

```cpp
for (i=0;i<lCount;i++)
    CoTaskMemFree(pKeys[i]);
```

Problem jest `i` zadeklarowany jako `UINT` i `lCount` jest zadeklarowany jako **`long`** , dlatego niezgodność ze znakiem/bez znaku. Nie można zmienić typu `lCount` do `UINT` , ponieważ pobiera jego wartość z `IMtsEventInfo::get_Count` , która używa typu **`long`** , i nie znajduje się w kodzie użytkownika. Dodajmy rzutowanie do kodu. Rzutowanie w stylu języka C wykona rzutowanie liczbowe, takie jak to, ale **`static_cast`** jest zalecanym stylem.

```cpp
for (i=0;i<static_cast<UINT>(lCount);i++)
    CoTaskMemFree(pKeys[i]);
```

Te ostrzeżenia są sytuacje, w których zmienna została zadeklarowana w funkcji, która ma parametr o tej samej nazwie, co prowadzi do potencjalnego mylącego kodu. Ustalono, że przez zmianę nazw zmiennych lokalnych.

### <a name="step-3-testing-and-debugging"></a>Krok 3. Testowanie i debugowanie

Aplikacja została najpierw przetestowana przez uruchomienie różnych menu i poleceń, a następnie zamknięcie aplikacji. Jedyny zauważony problem był potwierdzeniem debugowania po zamknięciu aplikacji. Problem pojawił się w destruktorze dla `CWindowImpl` klasy bazowej `CSpyCon` obiektu, główny składnik modelu COM aplikacji. Wystąpił błąd potwierdzenia w następującym kodzie w atlwin. h.

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

`hWnd`Zwykle jest ustawiona na zero w `WindowProc` funkcji, ale nie miało to miejsce, ponieważ zamiast domyślnego `WindowProc` , niestandardowa procedura obsługi jest wywoływana dla komunikatu systemu Windows (WM_SYSCOMMAND), który zamknie okno. Niestandardowa obsługa nie została ustawiona na `hWnd` wartość zero. Spójrz na podobny kod w `CWnd` klasie MFC, pokazuje, że gdy okno jest niszczone, `OnNcDestroy` jest wywoływana, i w MFC, dokumentacja doradza, że w przypadku przesłaniania `CWnd::OnNcDestroy` `NcDestroy` należy wywołać bazę, aby upewnić się, że wystąpiły odpowiednie operacje czyszczenia, w tym oddzielenie uchwytu okna z okna, lub innymi słowy, ustawienie `hWnd` na zero. To potwierdzenie mogło zostać wyzwolone w pierwotnej wersji próbki, ponieważ ten sam kod potwierdzania był obecny w starej wersji atlwin. h.

W celu przetestowania funkcjonalności aplikacji został utworzony **składnik usługi** przy użyciu szablonu projektu ATL, który został wybrany do dodania obsługi modelu COM+ w Kreatorze projektu ATL. Jeśli wcześniej nie pracowałeś z serwisowanymi składnikami, nie jest to trudne do utworzenia i udostępnienia w systemie lub w sieci innych aplikacji do użycia. Aplikacja COM Spy została zaprojektowana tak, aby monitorować aktywność składników usługi jako pomoc diagnostyczną.

Następnie dodaliśmy klasę, wybierz obiekt ATL i określ nazwę obiektu jako `Dog` . Następnie w Dog. h i Dog. cpp dodaliśmy implementację.

```cpp
STDMETHODIMP CDog::Wag(LONG* lDuration)
{
    // TODO: Add your implementation code here
    *lDuration = 100l;
    return S_OK;
}
```

Następnie został utworzony i zarejestrowany (należy uruchomić program Visual Studio jako administrator) i aktywować go przy użyciu aplikacji **składnika usługi** w panelu sterowania systemu Windows. Utworzyliśmy projekt w języku C# Windows Forms, przeciągając przycisk do formularza z przybornika i dwukrotnie kliknięty do obsługi zdarzeń kliknięcia. Dodaliśmy następujący kod w celu utworzenia wystąpienia `Dog` składnika.

```cpp
private void button1_Click(object sender, EventArgs e)
{
    ATLProjectLib.Dog dog1 = new ATLProjectLib.Dog();
    dog1.Wag();
}
```

Ta czynność została uruchomiona bez problemów, a model COM Spy działa i jest skonfigurowany do monitorowania `Dog` składnika, pojawi się wiele danych pokazujących działanie.

## <a name="see-also"></a>Zobacz także

[Przenoszenie i uaktualnianie: Przykłady i analizy przypadków](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[Następny przykład: Spy + +](../porting/porting-guide-spy-increment.md)<br/>
[Poprzedni przykład: Bazgroły MFC](../porting/porting-guide-mfc-scribble.md)
