---
title: CMFCAcceleratorKeyAssignCtrl Class
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: c6ce8c75b1b764d1d2b66b86147035f069805d25
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403915"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl Class

`CMFCAcceleratorKeyAssignCtrl` Klasa rozszerza [klasa CEdit](../../mfc/reference/cedit-class.md) do obsługi dodatkowych przycisków systemowych, takich jak ALT, CONTROL i SHIFT.

## <a name="syntax"></a>Składnia

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Konstruuje `CMFCAcceleratorKeyAssignCtrl` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Pobiera `ACCEL` struktury dla wciśnięty klawisz skrótu `CMFCAcceleratorKeyAssignCtrl` obiektu.|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Określa, czy klawisz skrótu został zdefiniowany.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do translacji komunikatów okien, zanim zostaną rozesłane do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkcje Windows. (Przesłania [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Resetuje klawisza skrótu.|

## <a name="remarks"></a>Uwagi

Ta klasa rozszerza funkcjonalność `CEdit` klasy dzięki obsłudze klawiszy skrótów, znany także jako klawiszy skrótów. `CMFCAcceleratorKeyAssignCtrl` Klasy funkcji jako [klasa CEdit](../../mfc/reference/cedit-class.md) i można go także rozpoznaje przycisków systemowych.

Ta klasa mapuje kombinacji klawiszy skrótów fizycznej do wartości typu ciąg. Załóżmy na przykład, kombinacja klawiszy ALT + B jest mapowany na ciąg "Alt + B". Gdy użytkownik naciśnie tej kombinacji klawiszy w `CMFCAcceleratorKeyAssignCtrl` obiektu "Alt + B" jest wyświetlany użytkownikowi. Aby uzyskać więcej informacji na temat mapowania między klawiszy skrótów i format ciągu, zobacz [klasa CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano sposób tworzenia `CMFCAcceleratorKeyAssignCtrl` obiektu i używać jej `ResetKey` metodę, aby zresetować klawisza skrótu.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxacceleratorkeyassignctrl.h

##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Konstruuje [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) obiektu.

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel

Pobiera `ACCEL` struktury dla wciśnięty klawisz skrótu [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) obiektu.

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Wartość zwracana

`ACCEL` Strukturę, która opisuje klawisza skrótu.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do pobierania `ACCEL` struktury klawisz skrótu, który użytkownik wprowadzi w swojej `CMFCAcceleratorKeyAssignCtrl` obiektu.

##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Określa, czy klawisz skrótu został zdefiniowany w [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) obiektu.

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli użytkownik nacisnął już prawidłową kombinację klawiszy, które definiują klawisza skrótu. w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określenia, czy użytkownik wprowadzi prawidłowy skrót klucza w swojej `CMFCAcceleratorKeyAssignCtrl` obiektu. Jeśli klawisz skrótu istnieje, możesz użyć [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) metodę, aby uzyskać `ACCEL` struktury skojarzona z tym kluczem skrótu.

##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w **VC\\atlmfc\\src\\mfc** folder instalacji programu Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

[in] *pMsg*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey

Resetuje klawisza skrótu.

```
void ResetKey();
```

### <a name="remarks"></a>Uwagi

Funkcja Usuwa tekst kontrolki edycji. Dotyczy to również wszelkich klawiszy skrótów, które użytkownik nacisnął klawisz.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)
