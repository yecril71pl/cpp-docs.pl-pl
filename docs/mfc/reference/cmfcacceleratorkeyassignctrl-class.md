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
ms.openlocfilehash: c7b60d9e695351e0c1d97b6629ff19664fcd6d05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369938"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Klasa CMFCAcceleratorKeyAssignCtrl

Klasa `CMFCAcceleratorKeyAssignCtrl` rozszerza [CEdit Klasy](../../mfc/reference/cedit-class.md) do obsługi dodatkowych przycisków systemowych, takich jak ALT, CONTROL i SHIFT.

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
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Pobiera strukturę `ACCEL` klawisza skrótu `CMFCAcceleratorKeyAssignCtrl` wciśniętego w obiekt.|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Określa, czy zdefiniowano klawisz skrótu.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Używane przez klasę [CWinApp](../../mfc/reference/cwinapp-class.md) do tłumaczenia wiadomości okna, zanim zostaną wysłane do [funkcji TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) i [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) systemu Windows. (Zastępuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Resetuje klawisz skrótu.|

## <a name="remarks"></a>Uwagi

Ta klasa rozszerza funkcjonalność `CEdit` klasy, obsługując klawisze skrótów, znane również jako klucze akceleratora. Klasa `CMFCAcceleratorKeyAssignCtrl` działa jako [CEdit Klasy](../../mfc/reference/cedit-class.md) i może również rozpoznawać przyciski systemowe.

Ta klasa mapuje fizyczne kombinacje klawiszy skrótów na wartości ciągu. Załóżmy na przykład, że kombinacja klawiszy ALT + B jest mapowana na ciąg "Alt + B". Gdy użytkownik naciśnie tę `CMFCAcceleratorKeyAssignCtrl` kombinację klawiszy w obiekcie, "Alt + B" jest wyświetlany użytkownikowi. Aby uzyskać więcej informacji na temat mapowania między klawiszami skrótów a formatem ciągu, zobacz [CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak skonstruować `CMFCAcceleratorKeyAssignCtrl` obiekt i użyć jego `ResetKey` metody, aby zresetować klawisz skrótu.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[Cedit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxacceleratorkeyassignctrl.h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Tworzy [obiekt CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel

Pobiera strukturę `ACCEL` klawisza skrótu wciśniętego w obiekcie [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Wartość zwracana

Struktura `ACCEL` opisująca klawisz skrótu.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do `ACCEL` pobierania struktury dla klawisza skrótu `CMFCAcceleratorKeyAssignCtrl` wprowadzonego przez użytkownika do obiektu.

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Określa, czy klucz skrótu został zdefiniowany w [obiekcie CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli użytkownik już nacisnął prawidłową kombinację klawiszy definiujących klawisz skrótu; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do określania, czy użytkownik `CMFCAcceleratorKeyAssignCtrl` wprowadził prawidłowy klawisz skrótu w obiekcie. Jeśli istnieje klawisz skrótu, można użyć [metody CMFCAcceleratorKeyAssignCtrl::GetAccel,](#getaccel) aby uzyskać strukturę skojarzoną `ACCEL` z tym klawiszem skrótu.

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Aby uzyskać więcej informacji, zobacz kod źródłowy znajdujący się w folderze **vc\\\\atlmfc src\\mfc** instalacji programu Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

[w] *pMsg*<br/>

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey

Resetuje klawisz skrótu.

```
void ResetKey();
```

### <a name="remarks"></a>Uwagi

Funkcja czyści tekst sterujący edycją. Obejmuje to wszystkie klawisze skrótów, które użytkownik nacisnął.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)
