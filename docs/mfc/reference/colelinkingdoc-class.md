---
title: COleLinkingDoc Class
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: c5076ceef0c6626fac0232fadf6818edd78b4ccf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773557"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc Class

Klasa podstawowa dla dokumentów kontenerów OLE, które obsługują łączenie elementów osadzonych, które zawierają.

## <a name="syntax"></a>Składnia

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Konstruuje `COleLinkingDoc` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleLinkingDoc::Register](#register)|Rejestruje dokumentu OLE systemowych bibliotek DLL.|
|[COleLinkingDoc::Revoke](#revoke)|Odwołuje rejestracji dokumentu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Wyszukuje określony element osadzony.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Wyszukuje określony element połączony.|

## <a name="remarks"></a>Uwagi

Aplikację kontenera, który obsługuje łączenie elementów osadzonych nosi nazwę "link container". [OCLIENT](../../overview/visual-cpp-samples.md) przykładowej aplikacji znajduje się przykład kontenera łącza.

Gdy połączony element źródłem jest element osadzony w innym dokumencie, że dokumentu zawierającego muszą być ładowane w kolejności osadzonego elementu do edycji. Z tego powodu należy mógł zostać uruchomiony przez inną aplikację kontenera, gdy użytkownik chce, aby edytować źródło połączony element kontenera łącze. Aplikacja musi także zostać użyta [element COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) klasy tak, aby móc tworzyć dokumenty, gdy uruchomiony programowo.

Aby kontenera kontenera łącza, pochodną klasy dokumentów z `COleLinkingDoc` zamiast [COleDocument](../../mfc/reference/coledocument-class.md). Podobnie jak w przypadku innych kontenerów OLE, należy zaprojektować klasy do przechowywania aplikacji natywnych danych także elementy osadzony lub połączony. Ponadto należy projektować struktur danych do przechowywania danych natywnych. Jeśli zdefiniujesz `CDocItem`-klasy pochodnej dla natywnych aplikacji danych, można użyć interfejsu zdefiniowane przez `COleDocument` do przechowywania danych natywnych, a także danych OLE.

Aby umożliwić aplikacji do uruchomienia programowo przy użyciu innego kontenera, należy zadeklarować `COleTemplateServer` obiektu jako członek aplikacji `CWinApp`-klasy pochodnej:

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

W `InitInstance` funkcji składowej typu usługi `CWinApp`-klasy, tworzenie szablonu dokumentu, a następnie określ swoje `COleLinkingDoc`-klasy jako klasa dokumentu:

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Połącz swoje `COleTemplateServer` obiektu do szablonów dokumentów przez wywołanie obiektu `ConnectTemplate` funkcja elementu członkowskiego i Zarejestruj wszystkie klasy obiektów w systemie OLE, wywołując `COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Przykład `CWinApp`-definicji klasy pochodnej i `InitInstance` funkcji, zobacz OCLIENT. H i OCLIENT. CPP próbki MFC [OCLIENT](../../overview/visual-cpp-samples.md).

Aby uzyskać więcej informacji na temat korzystania z `COleLinkingDoc`, zobacz artykuły [kontenerów: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md) i [kontenerów: Zaawansowane funkcje](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc

Konstruuje `COleLinkingDoc` obiektu bez komunikacji z OLE systemowych bibliotek DLL.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Uwagi

Należy wywołać `Register` funkcja elementu członkowskiego, aby informować OLE, czy dokument jest otwarty.

##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem

Metoda wywoływana przez platformę, by określić czy dokument zawiera wbudowanego elementu OLE przy użyciu określonej nazwy.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Wskaźnik na nazwę osadzonych obiektów OLE żądanego elementu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do określonego elementu; Wartość NULL, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Domyślna implementacja wyszukuje na liście elementów osadzonego elementu przy użyciu określonej nazwy (nazwa porównania jest uwzględniana wielkość liter). Należy przesłonić tę funkcję, jeśli ma zastosowanie własnej metody przechowywania lub nazewnictwa elementy osadzone OLE.

##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem

Metoda wywoływana przez platformę, by sprawdzić, czy dokument zawiera element połączony serwer o podanej nazwie.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Wskaźnik na nazwę połączonego OLE żądanego elementu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do określonego elementu; Wartość NULL, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Wartość domyślna `COleLinkingDoc` implementacji zawsze zwraca wartość NULL. Ta funkcja jest przesłonięta w pochodnej klasie `COleServerDoc` wyszukiwania na liście elementów serwera OLE dla połączonego elementu przy użyciu określonej nazwy (nazwa porównania jest uwzględniana wielkość liter). Należy przesłonić tę funkcję, jeśli udało Ci się wdrożyć swoją własną metodę, przechowywanie i pobieranie elementów połączonego serwera.

##  <a name="register"></a>  COleLinkingDoc::Register

Informuje system OLE bibliotek DLL, czy dokument jest otwarty.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*pFactory*<br/>
Wskaźnik do obiektu fabryki (może być NULL).

*lpszPathName*<br/>
Wskaźnik do pełni kwalifikowaną ścieżkę dokumentu kontenera.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli dokument został pomyślnie zarejestrowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję podczas tworzenia lub otwierania wskazanego pliku, aby zarejestrować dokument w systemie OLE biblioteki dll. Nie ma potrzeby aby wywołać tę funkcję, jeśli dokument reprezentuje element osadzony.

Jeśli używasz `COleTemplateServer` w aplikacji `Register` jest wywoływana w programie `COleLinkingDoc`przez implementację `OnNewDocument`, `OnOpenDocument`, i `OnSaveDocument`.

##  <a name="revoke"></a>  COleLinkingDoc::Revoke

Informuje system OLE bibliotek DLL, dokument jest już otwarty.

```
void Revoke();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby można było odwołać dokumentu rejestracji w systemie OLE biblioteki dll.

Podczas zamykania pliku o nazwie wywołać tę funkcję, ale zwykle nie trzeba bezpośrednio wywoływać. `Revoke` jest wywoływana przez `COleLinkingDoc`przez implementację `OnCloseDocument`, `OnNewDocument`, `OnOpenDocument`, i `OnSaveDocument`.

## <a name="see-also"></a>Zobacz także

[Próbki MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument Class](../../mfc/reference/coledocument-class.md)<br/>
[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)
