---
title: Klasa COleCmdUI
ms.date: 09/12/2018
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
ms.openlocfilehash: 1b7a6b21a3ad778b4a5ca345b1aaf42875810e4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376267"
---
# <a name="colecmdui-class"></a>Klasa COleCmdUI

Implementuje metodę MFC, aby zaktualizować stan obiektów interfejsu `IOleCommandTarget`użytkownika związanych z -driven funkcji aplikacji.

## <a name="syntax"></a>Składnia

```
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
|[COleCmdUI::Włącz](#enable)|Ustawia lub czyści flagę polecenia enable.|
|[COleCmdUI::SetCheck](#setcheck)|Ustawia stan polecenia włącz/wyłączanie przełącznika.|
|[COleCmdUI::SetText](#settext)|Zwraca nazwę tekstową lub ciąg stanu polecenia.|

## <a name="remarks"></a>Uwagi

W aplikacji, która nie jest włączona dla DocObjects, gdy użytkownik wyświetla menu w aplikacji, MFC przetwarza UPDATE_COMMAND_UI powiadamia. Każde powiadomienie otrzymuje [obiekt CCmdUI,](../../mfc/reference/ccmdui-class.md) który można manipulować w celu odzwierciedlenia stanu określonego polecenia. Jednak gdy aplikacja jest włączona dla DocObjects, MFC przetwarza UPDATE_OLE_COMMAND_UI `COleCmdUI` powiadomień i przypisuje obiekty.

`COleCmdUI`umożliwia DocObject odbierać polecenia, które pochodzą z interfejsu użytkownika kontenera (takich jak FileNew, Open, Print, itd.) i umożliwia kontenerowi odbieranie poleceń pochodzących z interfejsu użytkownika DocObject. Chociaż `IDispatch` może służyć do wysyłania `IOleCommandTarget` tych samych poleceń, zapewnia prostszy sposób wykonywania, ponieważ opiera się na standardowy zestaw poleceń, zwykle bez argumentów i nie jest zaangażowanych informacji o typie. `COleCmdUI`może służyć do włączania, aktualizowania i ustawiania innych właściwości poleceń interfejsu użytkownika DocObject. Jeśli chcesz wywołać polecenie, zadzwoń [do COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd).

Aby uzyskać więcej informacji na temat DocObjects, zobacz [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) i [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Ccmdui](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocobj.h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

Konstruuje `COleCmdUI` obiekt skojarzony z określonym poleceniem interfejsu użytkownika.

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>Parametry

*rgCmds*<br/>
Lista obsługiwanych poleceń skojarzonych z danym identyfikatorem GUID. Struktura `OLECMD` kojarzy polecenia z flagami poleceń.

*cCmds*<br/>
Liczba poleceń w *rgCmds*.

*pGrupa*<br/>
Wskaźnik do identyfikatora GUID, który identyfikuje zestaw poleceń.

### <a name="remarks"></a>Uwagi

Obiekt `COleCmdUI` udostępnia interfejs programowy do aktualizowania obiektów interfejsu użytkownika DocObject, takich jak elementy menu lub przyciski paska sterowania. Obiekty interfejsu użytkownika można włączyć, wyłączyć, sprawdzić i/lub wyczyścić `COleCmdUI` za pośrednictwem obiektu.

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI::Włącz

Wywołanie tej funkcji, aby `COleCmdUI` ustawić flagę polecenia obiektu do OLECOMDF_ENABLED, który informuje interfejs, że polecenie jest dostępne i włączone, lub wyczyścić flagę polecenia.

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>Parametry

*Bon*<br/>
Wskazuje, czy polecenie skojarzone `COleCmdUI` z obiektem powinno być włączone czy wyłączone. Nonzero włącza polecenie; 0 wyłącza polecenie.

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::SetCheck

Wywołanie tej funkcji, aby ustawić stan polecenia włącz/wyłączyć.

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>Parametry

*nSprawda*<br/>
Wartość określająca stan, aby ustawić polecenie włącz/wyłączanie przełącznika. Wartości to:

|Wartość|Opis|
|-----------|-----------------|
|**1**|Ustawia polecenie włączone.|
|**2**|Ustawia polecenie na nieokreślony; nie można ustalić stanu, ponieważ atrybut tego polecenia znajduje się zarówno w stanach włączonych, jak i wyłączonych w odpowiednim zaznaczeniu.|
|wszelkie inne wartości|Ustawia polecenie na wyłączone.|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI::SetText

Wywołanie tej funkcji, aby zwrócić nazwę tekstową lub ciąg stanu dla polecenia.

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parametry

*lpszText (tekst)*<br/>
Wskaźnik do tekstu, który ma być używany z poleceniem.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdUI](../../mfc/reference/ccmdui-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
