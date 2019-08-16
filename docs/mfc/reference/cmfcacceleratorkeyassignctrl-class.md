---
title: Klasa CMFCAcceleratorKeyAssignCtrl
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
ms.openlocfilehash: 5e57bf149fdbc293692c613afcabcf2d11d32221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505469"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Klasa CMFCAcceleratorKeyAssignCtrl

Klasa rozszerza klasę CEdit, aby obsługiwała dodatkowe przyciski systemowe, takie jak Alt, Control i Shift. [](../../mfc/reference/cedit-class.md) `CMFCAcceleratorKeyAssignCtrl`

## <a name="syntax"></a>Składnia

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Konstruuje `CMFCAcceleratorKeyAssignCtrl` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Pobiera strukturę klawisza skrótu naciśniętego `CMFCAcceleratorKeyAssignCtrl` w obiekcie. `ACCEL`|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Określa, czy klawisz skrótu został zdefiniowany.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do translacji komunikatów okna przed ich wysłaniem do funkcji [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. (Przesłania [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Resetuje klawisz skrótu.|

## <a name="remarks"></a>Uwagi

Ta Klasa rozszerza funkcjonalność `CEdit` klasy poprzez obsługę klawiszy skrótów, nazywanych również klawiszami akceleratora. Klasa działa jako [Klasa CEdit](../../mfc/reference/cedit-class.md) i może również rozpoznawać przyciski systemowe. `CMFCAcceleratorKeyAssignCtrl`

Ta klasa mapuje fizyczne kombinacje klawiszy skrótu na wartości ciągu. Załóżmy na przykład, że kombinacja klawiszy ALT + B jest zamapowana na ciąg "Alt + B". Gdy użytkownik naciśnie tę kombinację klawiszy w `CMFCAcceleratorKeyAssignCtrl` obiekcie, zostanie wyświetlony znak "Alt + B". Aby uzyskać więcej informacji na temat mapowania między skrótami klawiaturowymi i formatem ciągu, zobacz [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób konstruowania `CMFCAcceleratorKeyAssignCtrl` obiektu i używania jego `ResetKey` metody do resetowania klawisza skrótu.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxacceleratorkeyassignctrl. h

##  <a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Konstruuje obiekt [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel

Pobiera strukturę klawisza skrótu naciśniętego w obiekcie [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) `ACCEL`

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Wartość zwracana

`ACCEL` Struktura opisująca klawisz skrótu.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby pobrać `ACCEL` strukturę klawisza skrótu, który użytkownik wprowadził `CMFCAcceleratorKeyAssignCtrl` do obiektu.

##  <a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl:: isfocusd

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Określa, czy klawisz skrótu został zdefiniowany w obiekcie [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli użytkownik naciśnie już prawidłową kombinację kluczy, które definiują klawisz skrótu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Użyj tej funkcji, aby określić, czy użytkownik wprowadził prawidłowy klawisz skrótu w `CMFCAcceleratorKeyAssignCtrl` obiekcie. Jeśli istnieje klawisz skrótu, można użyć metody [CMFCAcceleratorKeyAssignCtrl:: GetAccel](#getaccel) , aby uzyskać `ACCEL` strukturę skojarzoną z tym klawiszem skrótu.

##  <a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::P reTranslateMessage

Aby uzyskać więcej szczegółów, zobacz kod źródłowy znajdujący się w folderze **VC\\atlmfc\\src\\MFC** instalacji programu Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

podczas *pMsg*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

##  <a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey

Resetuje klawisz skrótu.

```
void ResetKey();
```

### <a name="remarks"></a>Uwagi

Funkcja czyści tekst kontrolki edycji. Obejmuje to wszystkie klawisze skrótów naciśnięte przez użytkownika.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)
