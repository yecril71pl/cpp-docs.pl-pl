---
title: Klasa COleCmdUI
ms.date: 07/24/2020
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: c21d9b504656e6bba5ca693e57958743bb1b8309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233213"
---
# <a name="colecmdui-class"></a>Klasa COleCmdUI

Implementuje metodę dla MFC w celu zaktualizowania stanu obiektów interfejsu użytkownika związanych z funkcjami opartymi na `IOleCommandTarget` aplikacji.

## <a name="syntax"></a>Składnia

```cpp
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|Konstruuje `COleCmdUI` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleCmdUI:: Enable](#enable)|Ustawia lub czyści flagę polecenia Enable.|
|[COleCmdUI:: SetCheck](#setcheck)|Ustawia stan polecenia włączania/wyłączania.|
|[COleCmdUI::SetText](#settext)|Zwraca nazwę tekstu lub ciąg stanu dla polecenia.|

## <a name="remarks"></a>Uwagi

W aplikacji, która nie jest włączona dla usługi DocObjects, gdy użytkownik przegląda menu w aplikacji, procesy MFC UPDATE_COMMAND_UI powiadomień według. Każde powiadomienie otrzymuje obiekt [CCmdUI](../../mfc/reference/ccmdui-class.md) , który może być modyfikowany w celu odzwierciedlenia stanu konkretnego polecenia. Jeśli jednak aplikacja jest włączona dla DocObjects, procesy MFC UPDATE_OLE_COMMAND_UI powiadomienia i przypisują `COleCmdUI` obiekty.

`COleCmdUI`zezwala DocObject na odbieranie poleceń, które pochodzą z interfejsu użytkownika kontenera (takich jak FileNew, Otwórz, Drukuj itd.) i umożliwia kontenerowi otrzymywanie poleceń pochodzących z interfejsu użytkownika DocObject. Chociaż `IDispatch` może służyć do wysyłania tych samych poleceń, `IOleCommandTarget` zapewnia łatwiejszy sposób wykonywania zapytań i wykonywania, ponieważ opiera się na standardowym zestawie poleceń, zwykle bez argumentów, i nie ma żadnych informacji o typie. `COleCmdUI`może służyć do włączania, aktualizowania i ustawiania innych właściwości poleceń interfejsu użytkownika DocObject. Gdy chcesz wywołać polecenie, wywołaj [COleServerDoc:: OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Aby uzyskać więcej informacji na temat DocObjects, zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob. h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

Konstruuje `COleCmdUI` obiekt skojarzony z określonym interfejsem użytkownika.

```cpp
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parametry

*rgCmds*<br/>
Lista obsługiwanych poleceń skojarzonych z danym identyfikatorem GUID. `OLECMD`Struktura kojarzy polecenia z flagami poleceń.

*cCmds*<br/>
Liczba poleceń w *rgCmds*.

*pGroup*<br/>
Wskaźnik do identyfikatora GUID, który identyfikuje zestaw poleceń.

### <a name="remarks"></a>Uwagi

`COleCmdUI`Obiekt udostępnia interfejs programistyczny do aktualizowania DocObject obiektów interfejsu użytkownika, takich jak elementy menu lub przyciski paska sterowania. Obiekty interfejsu użytkownika można włączać, wyłączać, sprawdzać i/lub wyczyszczone za pomocą `COleCmdUI` obiektu.

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI:: Enable

Wywołaj tę funkcję, aby ustawić flagę polecenia `COleCmdUI` obiektu na OLECOMDF_ENABLED, co informuje interfejs, że polecenie jest dostępne i włączone, lub wyczyść flagę polecenia.

```cpp
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parametry

*bOn*<br/>
Wskazuje, czy polecenie skojarzone z `COleCmdUI` obiektem powinno być włączone czy wyłączone. Wartość różna od zera włącza polecenie; 0 wyłącza polecenie.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI:: SetCheck

Wywołaj tę funkcję, aby ustawić stan polecenia Włącz/Wyłącz.

```cpp
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nSprawdź*<br/>
Wartość określająca stan, aby ustawić włączenie/wyłączenie polecenia przełączania. Wartości to:

|Wartość|Opis|
|-----------|-----------------|
|**1**|Ustawia polecenie na wartość włączone.|
|**2**|Ustawia nieokreślony polecenie; nie można określić stanu, ponieważ atrybut tego polecenia jest włączony i wyłączony w odpowiednim zaznaczeniu.|
|dowolna inna wartość|Ustawia polecenie na off.|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI::SetText

Wywołaj tę funkcję, aby zwrócić nazwę tekstu lub ciąg stanu dla polecenia.

```cpp
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText*<br/>
Wskaźnik do tekstu, który ma być używany z poleceniem.

## <a name="see-also"></a>Zobacz także

[Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
