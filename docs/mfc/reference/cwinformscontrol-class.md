---
title: Klasa CWinFormsControl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 57a06fe87e7d4fbcf698cc333022c4c32afb40da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442607"
---
# <a name="cwinformscontrol-class"></a>Klasa CWinFormsControl

Oferuje podstawowe funkcje obsługi formantu Windows Forms.

## <a name="syntax"></a>Składnia

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Parametry

*TManagedControl*<br/>
Kontrolki formularzy Windows programu .NET Framework mają być wyświetlane w aplikacji MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Konstruuje obiekt otoki kontrolki formularzy Windows w MFC.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Tworzy formant programu Windows Forms w pojemniku MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Pobiera wskaźnik do kontrolki Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Pobiera uchwyt do kontrolki Windows Forms.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|Zastępuje [CWinFormsControl::GetControl](#getcontrol) w wyrażeniach.|
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|Rzutuje typu jako wskaźnik do formantu Windows Forms.|

## <a name="remarks"></a>Uwagi

`CWinFormsControl` Klasa oferuje podstawowe funkcje obsługi formantu Windows Forms.

Aby uzyskać więcej informacji na temat korzystania z Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Kod MFC nie pamięci podręcznej dojścia okna (zazwyczaj przechowywane w `m_hWnd`). Niektóre właściwości formantów formularzy Windows wymagają, aby bazowego Win32 `Window` zniszczone i ponownie utworzony przy użyciu `DestroyWindow` i `CreateWindow`. Uchwyty implementacji MFC Windows Forms `Destroy` i `Create` zdarzeń formantów, aby zaktualizować `m_hWnd` elementu członkowskiego.

> [!NOTE]
>  Integracja biblioteki MFC, formularzy Windows działa tylko w projektach, które dołączana dynamicznie z MFC (w którym jest zdefiniowany AFXDLL).

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxwinforms.h

##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl

Tworzy formant programu Windows Forms w pojemniku MFC.

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
Typ danych formantu, który ma zostać utworzony. Musi być [typu](https://msdn.microsoft.com/library/system.type) typu danych.

*dwStyle*<br/>
Styl okna, które dotyczą kontrolki. Określ kombinację [Style okna ramowego](../../mfc/reference/styles-used-by-mfc.md#window-styles). Obecnie obsługiwane są tylko następujące style: WS_TABSTOP, WS_VISIBLE, WS_DISABLED i WS_GROUP.

*Rect*<br/>
A [struktura RECT](../../mfc/reference/rect-structure1.md) definiujący współrzędne lewym i prawym dolnym rogu formantu (pierwsze przeciążenie tylko).

*nPlaceHolderID*<br/>
Uchwyt formant zastępczy statyczne miejsce umieszczone w edytorze zasobów. Nowo utworzonego formantu Windows Forms zastępuje statyczną kontrolkę, zakładając, że jego położenie, porządek i style (drugie przeciążenie tylko).

*pParentWnd*<br/>
Wskaźnik do okna nadrzędnego.

*nID*<br/>
Identyfikatora zasobu do przypisania do nowo utworzonego formantu.

*pControl*<br/>
Wystąpienie formantu Windows Forms do skojarzenia z [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) obiektu (tylko w przypadku przeciążenia czwarty).

### <a name="return-value"></a>Wartość zwracana

Jeśli to się powiedzie, zwraca wartość różną od zera. W przypadku niepowodzenia zwraca zero.

### <a name="remarks"></a>Uwagi

Ta metoda tworzy wystąpienie formantu .NET Framework Windows Forms w pojemniku MFC.

Pierwsze przeciążenie metody akceptuje typ danych .NET Framework *pType* tak, aby MFC można utworzyć wystąpienia nowego obiektu tego typu. *pType* musi być [typu](https://msdn.microsoft.com/library/system.type) typu danych.

Drugie przeciążenie metody tworzy formantu Windows Forms na podstawie `TManagedControl` parametru szablonu `CWinFormsControl` klasy. Rozmiar i położenie formantu opiera się na `RECT` struktury przekazany do metody. Tylko *dwStyle* ma znaczenie dla stylów.

Trzecie przeciążenie metody tworzy formant Windows Forms, który zastępuje formant statyczny niszczenie go przy założeniu, że jego położenie, porządek i style. Statyczny formantu służy tylko jako symbolu zastępczego formantu Windows Forms. Podczas tworzenia kontrolki, to przeciążenie łączy style z *dwStyle* ze stylami zasobów kontrolki statycznej.

Czwarty przeciążenia metody umożliwia przekazywanie już utworzona formantu Windows Forms *pControl* , który będzie zawijany w MFC. Musi być tego samego typu co `TManagedControl` parametru szablonu `CWinFormsControl` klasy.

Zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) przykładów na temat korzystania z formularza Windows kontrolki.

##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl

Konstruuje obiekt otoki kontrolki formularzy Windows w MFC.

```
CWinFormsControl();
```

### <a name="remarks"></a>Uwagi

Kontrolki Windows Forms, zostanie uruchomiony po wywołaniu [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrol"></a>  CWinFormsControl::GetControl

Pobiera wskaźnik do kontrolki Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do kontrolki Windows Forms.

### <a name="example"></a>Przykład

  Zobacz [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle

Pobiera uchwyt do kontrolki Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do kontrolki Windows Forms.

### <a name="remarks"></a>Uwagi

`GetControlHandle` jest metodą pomocnika, która zwraca uchwyt okna przechowywane we właściwościach formantu .NET Framework. Wartość dojścia okna jest kopiowany do [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) podczas wywołania [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).

##  <a name="operator_-_gt"></a>  CWinFormsControl::operator-&gt;

Zastępuje [CWinFormsControl::GetControl](#getcontrol) w wyrażeniach.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Uwagi

Ten operator miejsce wygodnej składni, która zastępuje `GetControl` w wyrażeniach.

Aby uzyskać więcej informacji na formularzach Windows Forms, zobacz [za pomocą kontrolki użytkownika formularza Windows w MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl ^

Rzutuje typu jako wskaźnik do formantu Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Uwagi

Ten operator przekazuje `CWinFormsControl<TManagedControl>` do funkcji, które akceptują wskaźnik do formantu Windows Forms.

## <a name="see-also"></a>Zobacz też

[Klasa CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Klasa CWinFormsView](../../mfc/reference/cwinformsview-class.md)
