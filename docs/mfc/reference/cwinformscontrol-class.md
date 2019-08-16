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
ms.openlocfilehash: 75a6d7ea2b4f3ab229d7e3f4d411711261bb1b82
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502195"
---
# <a name="cwinformscontrol-class"></a>Klasa CWinFormsControl

Zapewnia podstawowe funkcje hostingu kontrolki Windows Forms.

## <a name="syntax"></a>Składnia

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parametry

*TManagedControl*<br/>
Kontrolka Windows Forms .NET Framework, która ma być wyświetlana w aplikacji MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Konstruuje obiekt otoki formantu Windows Forms MFC.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Tworzy kontrolkę Windows Forms w kontenerze MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Pobiera wskaźnik do kontrolki Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Pobiera uchwyt do kontrolki Windows Forms.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::operator -&gt;](#operator_-_gt)|Zamienia [CWinFormsControl:: GetControl](#getcontrol) w wyrażeniach.|
|[CWinFormsControl::operator TManagedControl^](#operator_tmanagedcontrol)|Rzutuje typ jako wskaźnik do kontrolki Windows Forms.|

## <a name="remarks"></a>Uwagi

`CWinFormsControl` Klasa zawiera podstawowe funkcje hostingu kontrolki Windows Forms.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Kod MFC nie powinien buforować dojść okna (zwykle przechowywanych w `m_hWnd`programie). Niektóre właściwości kontrolki Windows Forms wymagają zniszczenia i ponownego `Window` utworzenia bazowego systemu Win32 przy użyciu `DestroyWindow` i `CreateWindow`. Implementacja MFC Windows Forms obsługuje `Destroy` i `Create` zdarzenia formantów w celu zaktualizowania `m_hWnd` elementu członkowskiego.

> [!NOTE]
>  Integracja MFC Windows Forms działa tylko w projektach, które łączą się dynamicznie z MFC (w którym zdefiniowano AFXDLL).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms. h

##  <a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl

Tworzy kontrolkę Windows Forms w kontenerze MFC.

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

*pType*<br/>
Typ danych formantu, który ma zostać utworzony. Musi być typem danych [typu](/dotnet/api/system.type) .

*dwStyle*<br/>
Styl okna, który ma zostać zastosowany do kontrolki. Określ kombinację [stylów okna](../../mfc/reference/styles-used-by-mfc.md#window-styles). Obecnie obsługiwane są tylko następujące style: WS_TABSTOP, WS_VISIBLE, WS_DISABLED i WS_GROUP.

*cinania*<br/>
[Struktura prostokąta](/windows/win32/api/windef/ns-windef-rect) , która definiuje współrzędne górnego lewego i prawego dolnego rogu kontrolki (tylko pierwszy przeciążenia).

*nPlaceHolderID*<br/>
Uchwyt statycznej kontrolki symbolu zastępczego umieszczony w edytorze zasobów. Nowo utworzona kontrolka Windows Forms zastępuje kontrolkę statyczną, przy założeniu, że jej pozycja, porządek osi i (tylko w drugim przeciążeniu).

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego.

*nID*<br/>
Numer identyfikatora zasobu, który ma zostać przypisany do nowo utworzonego formantu.

*pControl*<br/>
Wystąpienie formantu Windows Forms, które ma być skojarzone z obiektem [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (tylko w czwartym przeciążeniu).

### <a name="return-value"></a>Wartość zwracana

Jeśli powiedzie się, zwraca wartość różną od zera. Jeśli nie powiedzie się, zwraca wartość zero.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy wystąpienie .NET Framework formantu Windows Forms w kontenerze MFC.

Pierwsze Przeciążenie metody przyjmuje .NET Framework typu danych *pType* , aby MFC mógł utworzyć wystąpienie nowego obiektu tego typu. *pType* musi być typem danych [typu](/dotnet/api/system.type) .

Drugie Przeciążenie metody tworzy formant Windows Forms na podstawie `TManagedControl` parametru `CWinFormsControl` szablonu klasy. Rozmiar i położenie kontrolki bazuje na `RECT` strukturze przekazaną do metody. Tylko *dwStyle* kwestie dotyczące stylów.

Trzecie Przeciążenie metody tworzy formant Windows Forms, który zastępuje kontrolkę statyczną, niszczy ją i zakładając jej położenie, porządek osi i style. Formant statyczny służy tylko jako symbol zastępczy dla kontrolki Windows Forms. Podczas tworzenia kontrolki to Przeciążenie łączy style z *dwStyle* z stylami zasobów kontrolki statycznej.

Czwarte Przeciążenie metody umożliwia przekazanie już uruchomionego Windows Forms formantu *pControl* , który zostanie zawinięty przez MFC. Musi być tego samego typu co `TManagedControl` parametr `CWinFormsControl` szablonu klasy.

Zobacz [Używanie kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) dla przykładów na korzystanie z kontrolek formularza systemu Windows.

##  <a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl

Konstruuje obiekt otoki formantu Windows Forms MFC.

```
CWinFormsControl();
```

### <a name="remarks"></a>Uwagi

Kontrolka Windows Forms jest tworzona podczas wywoływania [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrol"></a>CWinFormsControl:: GetControl

Pobiera wskaźnik do kontrolki Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do kontrolki Windows Forms.

### <a name="example"></a>Przykład

  Zobacz [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

Pobiera uchwyt do kontrolki Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do kontrolki Windows Forms.

### <a name="remarks"></a>Uwagi

`GetControlHandle`to metoda pomocnika zwracająca uchwyt okna, który jest przechowywany we właściwościach kontrolki .NET Framework. Wartość uchwytu okna jest kopiowana do [CWnd:: m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) podczas wywołania do [CWnd:: Attach](../../mfc/reference/cwnd-class.md#attach).

##  <a name="operator_-_gt"></a>CWinFormsControl:: operator-&gt;

Zamienia [CWinFormsControl:: GetControl](#getcontrol) w wyrażeniach.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Uwagi

Ten operator udostępnia wygodną składnię zastępującą `GetControl` wyrażenia.

Aby uzyskać więcej informacji na Windows Forms, zobacz [Korzystanie z kontrolki użytkownika formularza systemu Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_tmanagedcontrol"></a>CWinFormsControl:: operator TManagedControl ^

Rzutuje typ jako wskaźnik do kontrolki Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Uwagi

Ten operator przechodzi `CWinFormsControl<TManagedControl>` do funkcji, które akceptują wskaźnik do kontrolki Windows Forms.

## <a name="see-also"></a>Zobacz także

[Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)
