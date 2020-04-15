---
title: Klasa CWinFormsControl
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: c91f50be1ea30efac81ff67c43633bedd7b0ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377182"
---
# <a name="cwinformscontrol-class"></a>Klasa CWinFormsControl

Zapewnia podstawowe funkcje hostingu formantu Windows Forms.

## <a name="syntax"></a>Składnia

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parametry

*Sterowanie TManagedcontrol*<br/>
Formant .NET Framework Windows Forms ma być wyświetlany w aplikacji MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Konstruuje obiekt otoki formantu formularzy MFC Windows.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Tworzy formant formularzy systemu Windows w kontenerze MFC.|
|[CWinFormsControl::Kontrola](#getcontrol)|Pobiera wskaźnik do formantu Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Pobiera dojście do formantu Windows Forms.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::operator -&gt;](#operator_-_gt)|Zastępuje [CWinFormsControl::GetControl](#getcontrol) w wyrażeniach.|
|[CWinFormsControl::operator TManagedControl^](#operator_tmanagedcontrol)|Rzutuje typ jako wskaźnik do formantu Windows Forms.|

## <a name="remarks"></a>Uwagi

Klasa `CWinFormsControl` zapewnia podstawowe funkcje hostingu formantu Windows Forms.

Aby uzyskać więcej informacji na temat korzystania z formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Kod MFC nie powinien buforować uchwytów `m_hWnd`okna (zwykle przechowywanych w ). Niektóre właściwości formantu formularzy systemu `Window` Windows wymagają zniszczenia i `DestroyWindow` odtworzenia podstawowej wersji Win32 przy użyciu programu . `CreateWindow` Implementacja MFC Windows Forms `Destroy` `Create` obsługuje zdarzenia i formantów, aby zaktualizować element członkowski. `m_hWnd`

> [!NOTE]
> Integracja formularzy systemu Windows MFC działa tylko w projektach, które łączą się dynamicznie z MFC (w którym jest zdefiniowana afxdll).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl

Tworzy formant formularzy systemu Windows w kontenerze MFC.

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>Parametry

*pTyp*<br/>
Typ danych formantu, który ma zostać utworzony. Musi być [typem](/dotnet/api/system.type) danych typu.

*Dwstyle*<br/>
Styl okna, aby zastosować do formantu. Określ kombinację [stylów okien](../../mfc/reference/styles-used-by-mfc.md#window-styles). Obecnie obsługiwane są tylko następujące style: WS_TABSTOP, WS_VISIBLE, WS_DISABLED i WS_GROUP.

*Rect*<br/>
[Struktura RECT,](/windows/win32/api/windef/ns-windef-rect) która definiuje współrzędne lewego górnego i prawego dolnego rogu formantu (tylko pierwsze przeciążenie).

*nPlaceHolderID*<br/>
Uchwyt statycznego uchwytu miejsca umieszczony w Edytorze zasobów. Nowo utworzony formant Windows Forms zastępuje formant statyczny, przyjmując jego położenie, kolejność z i style (tylko drugie przeciążenie).

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego.

*Nid*<br/>
Numer identyfikatora zasobu, który ma zostać przypisany do nowo utworzonego formantu.

*pKontroluj*<br/>
Wystąpienie formantu Windows Forms, który ma być skojarzony z obiektem [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (tylko czwarte przeciążenie).

### <a name="return-value"></a>Wartość zwracana

Jeśli się powiedzie, zwraca wartość niezerową. Jeśli nie powiedzie się, zwraca zero.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy wystąpienia formantu .NET Framework Windows Forms w kontenerze MFC.

Pierwsze przeciążenie metody akceptuje typ danych .NET Framework *pType,* dzięki czemu MFC można utworzyć wystąpienie nowego obiektu tego typu. *pType* musi być [typem](/dotnet/api/system.type) danych typu.

Drugie przeciążenie metody tworzy formant Windows `TManagedControl` Forms na `CWinFormsControl` podstawie parametru szablonu klasy. Rozmiar i położenie formantu opiera `RECT` się na strukturze przekazywane do metody. Tylko *dwStyle* ma znaczenie dla stylów.

Trzecie przeciążenie metody tworzy formant Windows Forms, który zastępuje formant statyczny, niszcząc go i przyjmując jego położenie, kolejność z i style. Formant statyczny służy tylko jako symbol zastępczy dla formantu Windows Forms. Podczas tworzenia formantu, to przeciążenie łączy style z *dwStyle* ze stylami zasobów formantu statycznego.

Czwarte przeciążenie metody umożliwia przekazywanie w już sułkowane windows forms kontroli *pControl,* że MFC zostanie zawinięty. Musi być tego samego typu `TManagedControl` co parametr `CWinFormsControl` szablonu klasy.

Zobacz [korzystanie z formantu użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) dla przykładów przy użyciu formantów formularza systemu Windows.

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl

Konstruuje obiekt otoki formantu formularzy MFC Windows.

```
CWinFormsControl();
```

### <a name="remarks"></a>Uwagi

Formant Windows Forms jest wywoływany podczas wywoływania [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>CWinFormsControl::Kontrola

Pobiera wskaźnik do formantu Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do formantu Windows Forms.

### <a name="example"></a>Przykład

  Zobacz [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

Pobiera dojście do formantu Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do formantu Windows Forms.

### <a name="remarks"></a>Uwagi

`GetControlHandle`jest metodą pomocniczą, która zwraca dojście okna przechowywane we właściwościach formantu .NET Framework. Wartość dojścia okna jest kopiowana do [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) podczas wywołania [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinFormsControl::operator -&gt;

Zastępuje [CWinFormsControl::GetControl](#getcontrol) w wyrażeniach.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Uwagi

Ten operator zapewnia wygodną składnię, która zastępuje `GetControl` w wyrażeniach.

Aby uzyskać więcej informacji na temat formularzy systemu Windows, zobacz [Korzystanie z formantu użytkownika formularza systemu Windows w programie MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinFormsControl::operator TManagedControl^

Rzutuje typ jako wskaźnik do formantu Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Uwagi

Ten operator `CWinFormsControl<TManagedControl>` przekazuje do funkcji, które akceptują wskaźnik do formantu Windows Forms.

## <a name="see-also"></a>Zobacz też

[Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)
