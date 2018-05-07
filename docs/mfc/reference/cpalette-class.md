---
title: Cpalette — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
dev_langs:
- C++
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 36cc13fa77becf5bdeb3960f6ac9db18d5d63dbb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cpalette-class"></a>Cpalette — klasa
Hermetyzuje palety kolorów systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CPalette : public CGdiObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPalette::CPalette](#cpalette)|Konstruuje `CPalette` obiektu z nie dołączonych palety systemu Windows. Należy zainicjować `CPalette` obiektu z jednej z funkcji Członkowskich inicjowania, zanim będzie można go używać.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CPalette::AnimatePalette](#animatepalette)|Zastępuje wpisów w logiczną paletę identyfikowane przez `CPalette` obiektu. Aplikacja nie ma można zaktualizować obszaru klienckiego, ponieważ Windows mapuje nowe wpisy w palecie systemu natychmiast.|  
|[CPalette::CreateHalftonePalette](#createhalftonepalette)|Paleta półtonów kontekstu urządzenia i dołącza go do `CPalette` obiektu.|  
|[CPalette::CreatePalette](#createpalette)|Tworzy palety kolorów systemu Windows i dołącza go do `CPalette` obiektu.|  
|[CPalette::FromHandle](#fromhandle)|Zwraca wskaźnik do `CPalette` obiektu, gdy uchwyt do obiektu palety systemu Windows.|  
|[CPalette::GetEntryCount](#getentrycount)|Pobiera liczbę wpisów palety w logiczną paletę.|  
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Zwraca indeks wpisu w palecie logiczne, która najlepiej pasuje do wartości koloru.|  
|[CPalette::GetPaletteEntries](#getpaletteentries)|Pobiera zakres wpisy palety w logiczną paletę.|  
|[CPalette::ResizePalette](#resizepalette)|Zmienia rozmiar logiczną paletę określony przez `CPalette` obiektu do określonej liczby wpisów.|  
|[CPalette::SetPaletteEntries](#setpaletteentries)|Ustawia flagi i wartości kolorów RGB w zakresie wpisów w logiczną paletę.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[HPALETTE CPalette::operator](#operator_hpalette)|Zwraca `HPALETTE` dołączony do `CPalette`.|  
  
## <a name="remarks"></a>Uwagi  
 Palety interfejs pomiędzy aplikacją i urządzenie wyjściowe kolorów (na przykład urządzenia wyświetlającego). Interfejs umożliwia aplikacji w pełni wykorzystać możliwości kolor urządzenia wyjściowego bez poważnie zakłócać kolorów wyświetlany przez inne aplikacje. System Windows używa aplikacji logiczną paletę (Lista kolory potrzebne) i palety systemu (który definiuje dostępne kolory) w celu określenia kolory używane.  
  
 A `CPalette` obiektu zapewnia funkcje Członkowskie manipulowanie palety określonych przez obiekt. Utworzyć `CPalette` obiektu i używać jej funkcji elementów członkowskich, do tworzenia rzeczywistych palety, obiekt graphics urządzenia (GDI) interfejsu i operowania nim wpisów i inne właściwości.  
  
 Aby uzyskać więcej informacji na temat używania `CPalette`, zobacz [obiektów graficznych](../../mfc/graphic-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxwin.h  
  
##  <a name="animatepalette"></a>  CPalette::AnimatePalette  
 Zastępuje wpisów w logiczną paletę dołączony do `CPalette` obiektu.  
  
```  
void AnimatePalette(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartIndex`  
 Określa pierwszą pozycję w palecie to animowanie.  
  
 `nNumEntries`  
 Określa liczbę wpisów w palecie to animowanie.  
  
 `lpPaletteColors`  
 Wskazuje pierwszego elementu członkowskiego tablicy [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) struktury tak, aby zastąpić wpisy palety identyfikowane przez `nStartIndex` i `nNumEntries`.  
  
### <a name="remarks"></a>Uwagi  
 Gdy aplikacja wywołuje `AnimatePalette`, nie ma aktualizacji obszaru klienckiego, ponieważ Windows mapuje nowe wpisy w palecie systemu natychmiast.  
  
 `AnimatePalette` Funkcja spowoduje jedynie zmianę wpisów z **PC_RESERVED** Flaga w odpowiednich **palPaletteEntry** członkiem [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) — struktura dołączony do `CPalette` obiektu. Zobacz **LOGPALETTE** w zestawie SDK systemu Windows, aby uzyskać więcej informacji na temat tej struktury.  
  
##  <a name="cpalette"></a>  CPalette::CPalette  
 Konstruuje `CPalette` obiektu.  
  
```  
CPalette();
```  
  
### <a name="remarks"></a>Uwagi  
 Z obiektem nie jest brak palety dołączone do czasu wywołania `CreatePalette` dołączyć jeden.  
  
##  <a name="createhalftonepalette"></a>  CPalette::CreateHalftonePalette  
 Tworzy palety półtonów dla kontekstu urządzenia.  
  
```  
BOOL CreateHalftonePalette(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Identyfikuje kontekst urządzenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różne od zera, jeśli funkcja zakończyła się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Aplikacji powinien utworzyć palety półtonów, gdy ustawiono tryb stretching kontekstu urządzenia **PÓŁTONÓW**. Palety logicznej półtonów zwrócony przez [CreateHalftonePalette](http://msdn.microsoft.com/library/windows/desktop/dd183503) funkcji członkowskiej należy następnie można wybrać i zrealizowane do kontekstu urządzenia przed [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) lub [ StretchDIBits](http://msdn.microsoft.com/library/windows/desktop/dd145121) funkcja jest wywoływana.  
  
 Zobacz Windows SDK, aby uzyskać więcej informacji `CreateHalftonePalette` i **StretchDIBits**.  
  
##  <a name="createpalette"></a>  CPalette::CreatePalette  
 Inicjuje `CPalette` obiektu tworząc paletę kolorów logiczny systemu Windows i dołączenie go do `CPalette` obiektu.  
  
```  
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `lpLogPalette`  
 Wskazuje [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) struktury, który zawiera informacje o kolorów w palecie logiczne.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz Windows SDK, aby uzyskać więcej informacji **LOGPALETTE** struktury.  
  
##  <a name="fromhandle"></a>  CPalette::FromHandle  
 Zwraca wskaźnik do `CPalette` obiektu, gdy uchwyt do obiektu palety systemu Windows.  
  
```  
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```  
  
### <a name="parameters"></a>Parametry  
 `hPalette`  
 Dojście do paletę kolorów GDI systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CPalette` obiektu w przypadku powodzenia; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `CPalette` obiekt nie jest już dołączony do systemu Windows palety, tymczasowej `CPalette` obiekt jest tworzony i dołączyć. To tymczasowe `CPalette` obiekt jest prawidłowy tylko do momentu przy następnym aplikacja ma czas bezczynności w pętli jego zdarzeń, w czasu grafiki wszystkie tymczasowe obiekty zostaną usunięte. Innymi słowy tymczasowy obiekt jest prawidłowy tylko podczas przetwarzania komunikatu jedno okno.  
  
##  <a name="getentrycount"></a>  CPalette::GetEntryCount  
 Wywołaj tę funkcję elementu członkowskiego, aby pobrać liczbę wpisów w danym logiczną paletę.  
  
```  
int GetEntryCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wpisów w logiczną paletę.  
  
##  <a name="getnearestpaletteindex"></a>  CPalette::GetNearestPaletteIndex  
 Zwraca indeks wpisu w palecie logicznej, która najlepiej pasuje do wartości koloru.  
  
```  
UINT GetNearestPaletteIndex(COLORREF crColor) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `crColor`  
 Określa kolor, który ma zostać dopasowany.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks wpis w logiczną paletę. Wpis zawiera kolor, który najlepiej pasuje podany kolor.  
  
##  <a name="getpaletteentries"></a>  CPalette::GetPaletteEntries  
 Pobiera zakres wpisy palety w logiczną paletę.  
  
```  
UINT GetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nStartIndex`  
 Określa pierwszą pozycję w logiczną paletę do pobrania.  
  
 `nNumEntries`  
 Określa liczbę wpisów w logiczną paletę do pobrania.  
  
 `lpPaletteColors`  
 Wskazuje tablicę [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) struktury danych, aby otrzymać wpisy palety. Tablica musi zawierać co najmniej tyle struktur danych określony przez `nNumEntries`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wpisów pobranych z logiczną paletę; 0, jeśli funkcja nie powiodła się.  
  
##  <a name="operator_hpalette"></a>  HPALETTE CPalette::operator  
 Użyj tego operatora, aby uzyskać dojście Windows GDI dołączonych `CPalette` obiektu.  
  
```  
operator HPALETTE() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli się powiedzie, uchwyt do obiektu Windows GDI reprezentowany przez `CPalette` obiektu; w przeciwnym razie **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest operatora rzutowania obsługuje bezpośredniego użycia `HPALETTE` obiektu.  
  
 Aby uzyskać więcej informacji o korzystaniu z obiektów graficznych, zobacz artykuł [obiektów grafiki](http://msdn.microsoft.com/library/windows/desktop/dd144962) w zestawie Windows SDK.  
  
##  <a name="resizepalette"></a>  CPalette::ResizePalette  
 Zmienia rozmiar logiczną paletę dołączony do `CPalette` obiektu liczby wpisy określone przez `nNumEntries`.  
  
```  
BOOL ResizePalette(UINT nNumEntries);
```  
  
### <a name="parameters"></a>Parametry  
 `nNumEntries`  
 Określa liczbę wpisów w palecie po został zmieniony.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pomyślnie zmiany rozmiaru palety; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli aplikacja wymaga `ResizePalette` pozwala zmniejszyć paletę wpisy pozostałych po zmianie rozmiaru palety nie uległy zmianie. Jeśli aplikacja wywoła `ResizePalette` Aby powiększyć palety, wpisy palety dodatkowe są ustawione na kolor czarny (wartości czerwonemu, zielonemu i niebieska są wszystkie 0) i flag wszystkie dodatkowe wpisy są ustawione na 0.  
  
 Aby uzyskać więcej informacji na temat interfejsu API systemu Windows `ResizePalette`, zobacz [ResizePalette](http://msdn.microsoft.com/library/windows/desktop/dd162928) w zestawie Windows SDK.  
  
##  <a name="setpaletteentries"></a>  CPalette::SetPaletteEntries  
 Ustawia flagi i wartości kolorów RGB w zakresie wpisów w logiczną paletę.  
  
```  
UINT SetPaletteEntries(
    UINT nStartIndex,  
    UINT nNumEntries,  
    LPPALETTEENTRY lpPaletteColors);
```  
  
### <a name="parameters"></a>Parametry  
 `nStartIndex`  
 Określa pierwszą pozycję w logiczną paletę do ustawienia.  
  
 `nNumEntries`  
 Określa liczbę wpisów w logiczną paletę do ustawienia.  
  
 `lpPaletteColors`  
 Wskazuje tablicę [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) struktury danych, aby otrzymać wpisy palety. Tablica musi zawierać co najmniej tyle struktur danych określony przez `nNumEntries`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wpisów w logiczną paletę; 0, jeśli funkcja nie powiodła się.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli logiczną paletę zostanie wybrane do kontekstu urządzenia, gdy aplikacja wywołuje `SetPaletteEntries`, zmiany zostaną uwzględnione po wywołania aplikacji [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette).  
  
 Aby uzyskać więcej informacji na temat struktury Windows **PALETTEENTRY**, zobacz [PALETTEENTRY](http://msdn.microsoft.com/library/windows/desktop/dd162769) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC DIBLOOK](../../visual-cpp-samples.md)   
 [Klasa CGdiObject](../../mfc/reference/cgdiobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](#getpaletteentries)   
 [CPalette::SetPaletteEntries](#setpaletteentries)



