---
title: Klasa CDocObjectServer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
dev_langs:
- C++
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 552252c8826e167b4aaa21aa41e489bbc8179ec3
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890378"
---
# <a name="cdocobjectserver-class"></a>Klasa CDocObjectServer

Implementuje dodatkowe interfejsy OLE potrzebne do normalnego `COleDocument` serwer do całego serwera obiektów DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, i `IPrint`.

## <a name="syntax"></a>Składnia

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Konstruuje `CDocObjectServer` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Aktywuje serwera obiektów dokumentu, ale nie jest wyświetlany.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|Wyświetla widok DocObject.|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Przywraca stan widoku DocObject.|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Zapisuje stan widoku DocObject.|

## <a name="remarks"></a>Uwagi

`CDocObjectServer` jest tworzony na podstawie `CCmdTarget` oraz ściśle współpracuje z `COleServerDoc` do udostępnienia interfejsów.

Dokument serwera obiektów DocObject może zawierać [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) obiektów, które reprezentują interfejs serwera obiektów DocObject elementów.

Aby dostosować swoje serwera obiektów DocObject, pochodną klasy z `CDocObjectServer` i zastąpić jej przeglądanie ustawień funkcji [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), i [OnSaveViewState ](#onsaveviewstate). Należy podać nowe wystąpienie klasy w odpowiedzi na wywołania framework.

Aby uzyskać więcej informacji na temat DocObjects zobacz [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) i [COleCmdUI](../../mfc/reference/colecmdui-class.md) w *odwołanie MFC*.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdocob.h

##  <a name="activatedocobject"></a>  CDocObjectServer::ActivateDocObject

Wywołaj tę funkcję, aby aktywować (ale nie pokazuj) serwera obiektów dokumentu.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Uwagi

`ActivateDocObject` wywołania `IOleDocumentSite`firmy `ActivateMe` metody, ale nie uwzględnia tego widoku, ponieważ czeka, aby uzyskać szczegółowe instrukcje na temat sposobu ustawiania i wyświetlania widoku, podany w wywołaniu [CDocObjectServer::OnActivateView](#onactivateview).

Razem `ActivateDocObject` i `OnActivateView` aktywacji i Wyświetl widok DocObject. Aktywacja DocObject różni się od innych rodzajów Aktywacja w miejscu OLE. Aktywacja DocObject Pomija wyświetlanie obramowanie kreskowania w miejscu i zakończeń obiektu (na przykład uchwytów zmiany rozmiaru), ignoruje obiektu zakresu funkcji i rysuje pasków przewijania w prostokącie widok, w przeciwieństwie do rysowania ich poza tym prostokąt (tak jak w normalnym Aktywacja w miejscu).

##  <a name="cdocobjectserver"></a>  CDocObjectServer::CDocObjectServer

Tworzy i inicjuje `CDocObjectServer` obiektu.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Parametry

*pOwner*<br/>
Wskaźnik do dokumentu lokacji klienta, który jest klienta dla serwera obiektów DocObject.

*pDocSite*<br/>
Wskaźnik do `IOleDocumentSite` interfejs implementowany przez kontener.

### <a name="remarks"></a>Uwagi

Gdy obiekt DocObject jest aktywny, klient lokacji interfejsu OLE ( `IOleDocumentSite`) umożliwia serwera obiektów DocObject do komunikowania się z jego klienta (kontenera). Po aktywowaniu serwera obiektów DocObject najpierw sprawdza on, że kontener implementuje `IOleDocumentSite` interfejsu. Jeśli tak, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) jest wywoływana, aby sprawdzić, czy kontener obsługuje DocObjects. Domyślnie `GetDocObjectServer` zwraca wartość NULL. Konieczne jest przesłonięcie `COleServerDoc::GetDocObjectServer` do utworzenia nowego `CDocObjectServer` obiekt lub pochodnej indywidualny charakter dzięki wskaźników do `COleServerDoc` kontenera i jego `IOleDocumentSite` interfejsu jako argumenty do konstruktora.

##  <a name="onactivateview"></a>  CDocObjectServer::OnActivateView

Wywołaj tę funkcję, aby wyświetlić widok DocObject.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca błąd lub ostrzeżenie wartość. Domyślnie zwraca brak błędu w przypadku powodzenia; w przeciwnym razie E_FAIL.

### <a name="remarks"></a>Uwagi

Ta funkcja tworzy okno ramowe w miejscu, rysuje paski przewijania w widoku, konfiguruje menu Serwer udostępnia z jego kontenerem, dodaje formantów ramkę, ustawia aktywnego obiektu, a następnie na końcu Pokazuje okno ramowe w miejscu i ustawia fokus.

##  <a name="onapplyviewstate"></a>  CDocObjectServer::OnApplyViewState

Należy przesłonić tę funkcję, aby przywrócić stan widoku DocObject.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Element `CArchive` obiektu, z którego można serializować stan widoku.

### <a name="remarks"></a>Uwagi

Ta funkcja jest wywoływana, gdy po raz pierwszy po jego wystąpienia wyświetlany jest widok. `OnApplyViewState` powoduje, że widok, aby zainicjował się ponownie zgodnie z danymi w `CArchive` wcześniej zapisana za pomocą obiektu [OnSaveViewState](#onsaveviewstate). Widok należy sprawdzić poprawność danych w `CArchive` obiektu, ponieważ kontenera nie jest podejmowana próba interpretować dane o stanie widoku w dowolny sposób.

Możesz użyć `OnSaveViewState` do przechowywania trwałe informacje specyficzne dla danego widoku stanu. Jeśli zastąpisz `OnSaveViewState` do przechowywania informacji, można zastąpić `OnApplyViewState` do odczytu informacji i zastosować je do widoku, gdy nowo jest aktywny.

##  <a name="onsaveviewstate"></a>  CDocObjectServer::OnSaveViewState

Należy przesłonić tę funkcję, aby zapisać dodatkowe informacje o widoku DocObject.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Parametry

*ar*<br/>
Element `CArchive` obiektu jest serializowana stan widoku.

### <a name="remarks"></a>Uwagi

Stan programu może zawierać właściwości, takie jak typ widoku, współczynnika powiększenia, wstawiania i punkcie wyboru i tak dalej. Kontener zazwyczaj wywołuje tę funkcję, zanim dezaktywowanie widoku. Zapisany stan można przywrócić później za pomocą [OnApplyViewState](#onapplyviewstate).

Możesz użyć `OnSaveViewState` do przechowywania trwałe informacje specyficzne dla danego widoku stanu. Jeśli zastąpisz `OnSaveViewState` do przechowywania informacji, można zastąpić `OnApplyViewState` do odczytu informacji i zastosować je do widoku, gdy nowo jest aktywny.

## <a name="see-also"></a>Zobacz też

[Klasa CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
