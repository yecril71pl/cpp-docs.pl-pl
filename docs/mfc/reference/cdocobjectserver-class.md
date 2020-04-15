---
title: Klasa CDocObjectServer
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: ccd8ddc9f4981b3d9f7f4e1decdf6790cd05b98b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375492"
---
# <a name="cdocobjectserver-class"></a>Klasa CDocObjectServer

Implementuje dodatkowe interfejsy OLE potrzebne `COleDocument` do wprowadzenia normalnego serwera do `IOleDocument`pełnego `IOleDocumentView` `IOleCommandTarget`serwera `IPrint`DocObject: , , i .

## <a name="syntax"></a>Składnia

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Serwer CDocObjectServer::SERWER CDocObjectServer](#cdocobjectserver)|Konstruuje `CDocObjectServer` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Serwer CDocObjectServer::ActivateDocObject](#activatedocobject)|Aktywuje serwer obiektów dokumentów, ale go nie wyświetla.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[Serwer CDocObjectServer::OnActivateView](#onactivateview)|Wyświetla widok DocObject.|
|[Serwer CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Przywraca stan widoku DocObject.|
|[Serwer CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Zapisuje stan widoku DocObject.|

## <a name="remarks"></a>Uwagi

`CDocObjectServer`pochodzi z `CCmdTarget` i ściśle współpracuje `COleServerDoc` z, aby udostępnić interfejsy.

Dokument serwera DocObject może zawierać obiekty [CDocObjectServerItem,](../../mfc/reference/cdocobjectserveritem-class.md) które reprezentują interfejs serwera do elementów DocObject.

Aby dostosować serwer DocObject, należy wyprowadzić `CDocObjectServer` własną klasę z funkcji konfiguracji widoku, [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate)i [OnSaveViewState.](#onsaveviewstate) Należy podać nowe wystąpienie klasy w odpowiedzi na wywołania framework.

Aby uzyskać więcej informacji na temat DocObjects, zobacz [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) i [COleCmdUI](../../mfc/reference/colecmdui-class.md) w *odwołaniu MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob.h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a>Serwer CDocObjectServer::ActivateDocObject

Wywołanie tej funkcji, aby aktywować (ale nie pokazać) serwer obiektów dokumentu.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Uwagi

`ActivateDocObject`wywołuje `IOleDocumentSite`metodę, ale nie pokazuje widoku, ponieważ czeka na konkretne instrukcje dotyczące konfigurowania i wyświetlania `ActivateMe` widoku, podane w wywołaniu [CDocObjectServer::OnActivateView](#onactivateview).

Razem `ActivateDocObject` i `OnActivateView` uaktywnić i wyświetlić widok DocObject. Aktywacja DocObject różni się od innych rodzajów aktywacji OLE w miejscu. Aktywacja DocObject pomija wyświetlanie obramowań kreskowania w miejscu i ozdób obiektów (takich jak uchwyty zmiany rozmiaru), ignoruje funkcje zasięgu obiektu i rysuje paski przewijania w prostokącie widoku, w przeciwieństwie do rysowania ich poza tym prostokątem (jak w normalnej aktywacji w miejscu).

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a>Serwer CDocObjectServer::SERWER CDocObjectServer

Konstruuje i inicjuje `CDocObjectServer` obiekt.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Parametry

*p Właściciel*<br/>
Wskaźnik do dokumentu lokacji klienta, który jest klientem serwera DocObject.

*pDocSite*<br/>
Wskaźnik do `IOleDocumentSite` interfejsu zaimplementowanego przez kontener.

### <a name="remarks"></a>Uwagi

Gdy DocObject jest aktywny, interfejs OLE `IOleDocumentSite`lokacji klienta ( ) jest to, co pozwala serwerowi DocObject do komunikowania się z jego klienta (kontener). Po aktywowaniu serwera DocObject najpierw sprawdza, czy kontener `IOleDocumentSite` implementuje interfejs. Jeśli tak, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) jest wywoływana, aby sprawdzić, czy kontener obsługuje DocObjects. Domyślnie `GetDocObjectServer` zwraca wartość NULL. Należy `COleServerDoc::GetDocObjectServer` zastąpić, aby utworzyć `CDocObjectServer` nowy obiekt lub obiekt pochodny własnego, ze `COleServerDoc` wskaźnikami `IOleDocumentSite` do kontenera i jego interfejsu jako argumenty do konstruktora.

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a>Serwer CDocObjectServer::OnActivateView

Wywołanie tej funkcji, aby wyświetlić widok DocObject.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość błędu lub ostrzeżenia. Domyślnie zwraca NOERROR, jeśli zakończy się pomyślnie; w przeciwnym razie E_FAIL.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy okno ramki w miejscu, rysuje paski przewijania w widoku, konfiguruje menu współudział serwera z kontenerem, dodaje formanty ramki, ustawia aktywny obiekt, a następnie na koniec pokazuje okno ramki w miejscu i ustawia fokus.

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a>Serwer CDocObjectServer::OnApplyViewState

Zastąpuj tę funkcję, aby przywrócić stan widoku DocObject.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
Obiekt, `CArchive` z którego można serializować stan widoku.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana, gdy widok jest wyświetlany po raz pierwszy po jego wystąpienia. `OnApplyViewState`nakazuje widok, aby ponownie zainicjować się zgodnie `CArchive` z danymi w obiekcie wcześniej zapisane z [OnSaveViewState](#onsaveviewstate). Widok musi sprawdzić poprawność `CArchive` danych w obiekcie, ponieważ kontener nie próbuje interpretować danych o stanie widoku w jakikolwiek sposób.

Za pomocą `OnSaveViewState` funkcji przechowywania trwałych informacji specyficznych dla stanu widoku. Jeśli zastąpisz `OnSaveViewState` do przechowywania informacji, należy `OnApplyViewState` zastąpić, aby przeczytać te informacje i zastosować je do widoku, gdy jest nowo aktywowany.

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a>Serwer CDocObjectServer::OnSaveViewState

Zastąpuj tę funkcję, aby zapisać dodatkowe informacje o stanie widoku DocObject.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*Ar*<br/>
Obiekt, `CArchive` do którego jest serializowany stan widoku.

### <a name="remarks"></a>Uwagi

Stan może obejmować właściwości, takie jak typ widoku, współczynnik powiększenia, punkt wstawiania i zaznaczenia itd. Kontener zazwyczaj wywołuje tę funkcję przed dezaktywacją widoku. Zapisany stan można później przywrócić za pomocą [OnApplyViewState](#onapplyviewstate).

Za pomocą `OnSaveViewState` funkcji przechowywania trwałych informacji specyficznych dla stanu widoku. Jeśli zastąpisz `OnSaveViewState` do przechowywania informacji, należy `OnApplyViewState` zastąpić, aby przeczytać te informacje i zastosować je do widoku, gdy jest nowo aktywowany.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
