---
title: Klasa CMFCAcceleratorKey
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: 7d66e7043325bbbd324f3ac443368787a653ebe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369928"
---
# <a name="cmfcacceleratorkey-class"></a>Klasa CMFCAcceleratorKey

Klasa pomocnika, która implementuje mapowanie i formatowanie kluczy wirtualnych.

## <a name="syntax"></a>Składnia

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Konstruuje `CMFCAcceleratorKey` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|Tłumaczy strukturę ACCEL na jej wizualną reprezentację.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Ustawia klawisz skrótu `CMFCAcceleratorKey` obiektu.|

## <a name="remarks"></a>Uwagi

Klawisze akceleratora są również nazywane klawiszami skrótów. Jeśli chcesz wyświetlić skróty klawiaturowe wprowadzane przez użytkownika, [klasa CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapuje skróty klawiaturowe, takie jak Alt+Shift+S, do niestandardowego formatu tekstowego, takiego jak "Alt + Shift + S". Każdy `CMFCAcceleratorKey` obiekt mapuje pojedynczy klawisz skrótu do formatu tekstu.

Aby uzyskać więcej informacji na temat używania klawiszy skrótów i tabel akceleratora, zobacz [CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak `CMFCAcceleratorKey` skonstruować `Format` obiekt i jak używać jego metody.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxacceleratorkey.h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey

Konstruuje [obiekt CMFCAcceleratorKey.](../../mfc/reference/cmfcacceleratorkey-class.md)

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parametry

*lpAccel (lpAccel)*<br/>
[w] Wskaźnik do klawisza skrótu.

### <a name="remarks"></a>Uwagi

Jeśli podczas tworzenia klawisza skrótu `CMFCAccleratorKey`nie jest podasz klawisz skrótu, użyj metody [CMFCAcceleratorKey::SetAccelerator,](#setaccelerator) aby skojarzyć klawisz skrótu z obiektem. `CMFCAcceleratorKey`

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a>CMFCAcceleratorKey::Format

Tłumaczy strukturę ACCEL na skojarzoną ją wartość ciągu.

```
void Format(CString& str) const;
```

### <a name="parameters"></a>Parametry

*Str*<br/>
[na zewnątrz] Odwołanie do `CString` obiektu, w którym metoda zapisuje przełożony klawisz skrótu.

### <a name="remarks"></a>Uwagi

Ta metoda pobiera format ciągu skojarzonego klawisza skrótu. Format ciągu obiektu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) można ustawić przy użyciu konstruktora lub metody [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator

Ustawia klawisz skrótu dla obiektu [CMFCAcceleratorKey.](../../mfc/reference/cmfcacceleratorkey-class.md)

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parametry

*lpAccel (lpAccel)*<br/>
[w] Wskaźnik do klawisza skrótu.

### <a name="remarks"></a>Uwagi

Ta metoda służy do ustawiania `CMFCAcceleratorKey` klawisza skrótu, jeśli podczas `CMFCAcceleratorKey`tworzenia programu nie podasz klawisza skrótu .

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy](../../mfc/reference/mfc-classes.md)<br/>
[Klasa CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
