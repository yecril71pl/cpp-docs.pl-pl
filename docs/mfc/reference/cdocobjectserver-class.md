---
title: Klasa CDocObjectServer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 912262c4f1ba85c181bb30ee5d6f38a0defe5d5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdocobjectserver-class"></a>Klasa CDocObjectServer
Implementuje dodatkowe interfejsy OLE potrzebne do podejmowania zwykłym `COleDocument` serwera do całego serwera DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`, i `IPrint`.  
  
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
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Aktywuje serwera obiektów dokumentu, ale nie są wyświetlane.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CDocObjectServer::OnActivateView](#onactivateview)|Wyświetla widok DocObject.|  
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Przywraca stan widoku DocObject.|  
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Zapisuje stan widoku DocObject.|  
  
## <a name="remarks"></a>Uwagi  
 `CDocObjectServer`jest pochodną `CCmdTarget` oraz ściśle współpracuje z `COleServerDoc` do udostępnienia interfejsy.  
  
 Dokument serwera DocObject może zawierać [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) obiektów, które reprezentują DocObject elementów interfejsu serwera.  
  
 Aby dostosować serwera DocObject, pochodzi z klasy z `CDocObjectServer` i zastąp jego funkcje ustawienia widoku [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), i [OnSaveViewState ](#onsaveviewstate). Należy podać nowe wystąpienie klasy w odpowiedź na wywołania framework.  
  
 Aby uzyskać więcej informacji o DocObjects zobacz [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) i [COleCmdUI](../../mfc/reference/colecmdui-class.md) w *odwołania MFC*. Zobacz też [pierwsze kroki Internet: dokumenty aktywne](../../mfc/active-documents-on-the-internet.md) i [dokumenty aktywne](../../mfc/active-documents-on-the-internet.md).  
  
 Zobacz też następujące artykułu bazy wiedzy:  
  
-   Q247382: PRB: etykietki narzędzi dla formantów ActiveX dokumentu Server są ukryte przez kontener dokumentu ActiveX  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 `CDocObjectServer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdocob.h  
  
##  <a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject  
 Wywołanie tej funkcji, aby aktywować (ale nie pokazuj) na serwerze obiektu dokumentu.  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Uwagi  
 `ActivateDocObject`wywołania `IOleDocumentSite`w **ActivateMe** metody, ale nie są wyświetlane w widoku, ponieważ oczekuje, aby uzyskać szczegółowe instrukcje na temat sposobu ustawiania i Wyświetl widok, podany w wywołaniu [CDocObjectServer::OnActivateView](#onactivateview).  
  
 Razem `ActivateDocObject` i `OnActivateView` aktywować i Wyświetl widok DocObject. Aktywacja DocObject różni się od innych rodzajów Aktywacja w miejscu OLE. Aktywacja DocObject Pomija wyświetlanie obramowanie kreskowania w miejscu i skojarzenia obiektu (na przykład uchwytów), ignoruje obiektu zakresu funkcji i rysuje paski przewijania w prostokącie widoku, a nie ich rysowania poza tym prostokącie (tak jak zwykle Aktywacja w miejscu).  
  
##  <a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer  
 Tworzy i inicjuje `CDocObjectServer` obiektu.  
  
```  
explicit CDocObjectServer(
    COleServerDoc* pOwner,  
    LPOLEDOCUMENTSITE pDocSite = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pOwner*  
 Wskaźnik do dokumentu lokacji klienta, który jest klienta dla serwera DocObject.  
  
 `pDocSite`  
 Wskaźnik do `IOleDocumentSite` interfejsu zaimplementowanego przez kontener.  
  
### <a name="remarks"></a>Uwagi  
 Gdy DocObject jest aktywny, klient lokacji interfejsu OLE ( `IOleDocumentSite`) to, co umożliwia serwerowi DocObject komunikację z klienta (kontener). Po aktywowaniu serwera DocObject najpierw sprawdza, czy kontener implementuje `IOleDocumentSite` interfejsu. Jeśli tak, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) jest wywoływana, aby sprawdzić, czy kontener obsługuje DocObjects. Domyślnie `GetDocObjectServer` zwraca **NULL**. Konieczne jest przesłonięcie `COleServerDoc::GetDocObjectServer` do utworzenia nowego `CDocObjectServer` obiektu lub pochodny samodzielnie, wskaźników do `COleServerDoc` kontenera i jego `IOleDocumentSite` interfejsu jako argumenty konstruktora.  
  
##  <a name="onactivateview"></a>CDocObjectServer::OnActivateView  
 Wywołanie tej funkcji, aby wyświetlić widok DocObject.  
  
```  
virtual HRESULT OnActivateView();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca błąd lub ostrzeżenie wartość. Domyślnie zwraca **brak błędu** przypadku powodzenia; w przeciwnym razie **E_FAIL**.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja tworzy okno ramowe w miejscu, rysuje pasków przewijania w widoku, konfiguruje menu Serwer udostępnia jego kontenera, dodaje formantów ramkę, ustawia aktywny obiekt, a następnie na koniec Pokazuje okno ramowe w miejscu i ustawia fokus.  
  
##  <a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState  
 Należy przesłonić tę funkcję, aby przywrócić stan widoku DocObject.  
  
```  
virtual void OnApplyViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 A `CArchive` obiektu, z którego można serializować stanu widoku.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest wywoływana, gdy widok jest wyświetlany po raz pierwszy po jego wystąpienia. `OnApplyViewState`powoduje, że widok może ponownie zainicjować się zgodnie z danymi w `CArchive` wcześniej zapisane przy użyciu obiektu [OnSaveViewState](#onsaveviewstate). Widok musi sprawdzić poprawności danych w `CArchive` obiektu, ponieważ kontenera nie jest podejmowana próba interpretować dane stanu widoku w dowolny sposób.  
  
 Można użyć `OnSaveViewState` do przechowywania trwałych informacje specyficzne dla danego widoku stanu. Jeśli można zastąpić `OnSaveViewState` do przechowywania informacji, można zastąpić `OnApplyViewState` do odczytu informacji i zastosować je do widoku, gdy nowo jest aktywny.  
  
##  <a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState  
 Należy przesłonić tę funkcję, aby zapisać informacje dodatkowe stan widoku DocObject.  
  
```  
virtual void OnSaveViewState(CArchive& ar);
```  
  
### <a name="parameters"></a>Parametry  
 `ar`  
 A `CArchive` obiekt, do którego serializowany jest stan widoku.  
  
### <a name="remarks"></a>Uwagi  
 Nazwa stanu może zawierać właściwości, takie jak typ widoku, współczynnika powiększenia, wstawiania i punkt wyboru i tak dalej. Kontener wywołuje zwykle ta funkcja przed dezaktywowanie widoku. Później można przywrócić zapisanego stanu za pośrednictwem [OnApplyViewState](#onapplyviewstate).  
  
 Można użyć `OnSaveViewState` do przechowywania trwałych informacje specyficzne dla danego widoku stanu. Jeśli można zastąpić `OnSaveViewState` do przechowywania informacji, można zastąpić `OnApplyViewState` do odczytu informacji i zastosować je do widoku, gdy nowo jest aktywny.  
  
## <a name="see-also"></a>Zobacz też  
 [CCmdTarget — klasa](../../mfc/reference/ccmdtarget-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)
