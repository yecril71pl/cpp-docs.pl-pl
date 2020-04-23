---
title: Klasa COleLinkingDoc
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
ms.openlocfilehash: 1fad986b7e7304075cacb0b5ced9feeb8af4664f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753849"
---
# <a name="colelinkingdoc-class"></a>Klasa COleLinkingDoc

Klasa podstawowa dla dokumentów kontenera OLE, które obsługują łączenie z elementami osadzonymi, które zawierają.

## <a name="syntax"></a>Składnia

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|Konstruuje `COleLinkingDoc` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleLinkingDoc::Zarejestruj się](#register)|Rejestruje dokument z bibliotekami DLL systemu OLE.|
|[COleLinkingDoc::Odwołaj](#revoke)|Odwołuje rejestrację dokumentu.|

### <a name="protected-methods"></a>Metody chronione

|Nazwa|Opis|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Znajduje określony element osadzony.|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Znajduje określony element połączony.|

## <a name="remarks"></a>Uwagi

Aplikacja kontenera, która obsługuje łączenie z elementami osadzonymi, jest nazywana "kontenerem łączy". Przykładowa aplikacja [OCLIENT](../../overview/visual-cpp-samples.md) jest przykładem kontenera łącza.

Gdy źródło elementu połączonego jest elementem osadzonym w innym dokumencie, dokument zawierający dokument musi zostać załadowany, aby element osadzony był edytowany. Z tego powodu kontener łącza musi być w stanie zostać uruchomiony przez inną aplikację kontenera, gdy użytkownik chce edytować źródło elementu połączonego. Aplikacja musi również używać [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) klasy, dzięki czemu można tworzyć dokumenty po uruchomieniu programowo.

Aby kontener był kontenerem łączy, należy `COleLinkingDoc` wyprowadzić klasę dokumentu z zamiast [COleDocument](../../mfc/reference/coledocument-class.md). Podobnie jak w przypadku każdego innego kontenera OLE, należy zaprojektować klasę do przechowywania danych natywnych aplikacji, a także elementów osadzonych lub połączonych. Ponadto należy zaprojektować struktury danych do przechowywania danych natywnych. Jeśli zdefiniujesz klasę pochodną `CDocItem`dla danych natywnych aplikacji, `COleDocument` można użyć interfejsu zdefiniowanego przez do przechowywania danych natywnych, a także danych OLE.

Aby umożliwić programowe uruchamianie aplikacji przez inny `COleTemplateServer` kontener, należy zadeklarować obiekt `CWinApp`jako element członkowski klasy pochodnej aplikacji:

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

W `InitInstance` funkcji elementu `CWinApp`członkowskiego klasy pochodnej utwórz szablon `COleLinkingDoc`dokumentu i określ klasę pochodną jako klasę dokumentu:

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

Połącz `COleTemplateServer` obiekt z szablonami dokumentów, wywołując `ConnectTemplate` funkcję elementu członkowskiego obiektu i rejestruj `COleTemplateServer::RegisterAll`wszystkie obiekty klasy w systemie OLE, wywołując:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

Aby uzyskać `CWinApp`przykładową definicję `InitInstance` i funkcję klasy pochodnej, zobacz OCLIENT. H i OCLIENT. CPP w próbce MFC [OCLIENT](../../overview/visual-cpp-samples.md).

Aby uzyskać więcej `COleLinkingDoc`informacji na temat używania , zobacz artykuły [Kontenery: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md) i [kontenerów: Zaawansowane funkcje](../../mfc/containers-advanced-features.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Cdocument](../../mfc/reference/cdocument-class.md)

[Coledocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxole.h

## <a name="colelinkingdoccolelinkingdoc"></a><a name="colelinkingdoc"></a>COleLinkingDoc::COleLinkingDoc

Konstruuje `COleLinkingDoc` obiekt bez rozpoczynania komunikacji z bibliotekami DLL systemu OLE.

```
COleLinkingDoc();
```

### <a name="remarks"></a>Uwagi

Należy wywołać `Register` funkcję elementu członkowskiego, aby poinformować OLE, że dokument jest otwarty.

## <a name="colelinkingdoconfindembeddeditem"></a><a name="onfindembeddeditem"></a>COleLinkingDoc::OnFindEmbeddedItem

Wywoływane przez strukturę, aby ustalić, czy dokument zawiera osadzony element OLE o określonej nazwie.

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Wskaźnik do nazwy żądanego elementu osadzonego OLE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do określonego elementu; NULL, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Domyślna implementacja przeszukuje listę elementów osadzonych dla elementu o określonej nazwie (porównanie nazw jest rozróżniane wielkości liter). Zastąd w tej funkcji, jeśli masz własną metodę przechowywania lub nazewnictwa osadzonych elementów OLE.

## <a name="colelinkingdocongetlinkeditem"></a><a name="ongetlinkeditem"></a>COleLinkingDoc::OnGetLinkedItem

Wywoływane przez strukturę, aby sprawdzić, czy dokument zawiera element serwera połączonego o określonej nazwie.

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>Parametry

*lpszItemName*<br/>
Wskaźnik do nazwy połączonego żądanego elementu OLE.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do określonego elementu; NULL, jeśli element nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Domyślna `COleLinkingDoc` implementacja zawsze zwraca wartość NULL. Ta funkcja jest zastępowana w `COleServerDoc` klasie pochodnej, aby przeszukiwać listę elementów serwera OLE dla połączonego elementu o określonej nazwie (w porównaniu nazw jest rozróżniana wielkość liter). Zastąd w tej funkcji zaimplementowano własną metodę przechowywania lub pobierania połączonych elementów serwera.

## <a name="colelinkingdocregister"></a><a name="register"></a>COleLinkingDoc::Zarejestruj się

Informuje biblioteki DLL systemu OLE, że dokument jest otwarty.

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parametry

*pFactory (Fabryka)*<br/>
Wskaźnik do obiektu fabrycznego OLE (może to być null).

*lpszPathName (nazwa lpszPathName)*<br/>
Wskaźnik do w pełni kwalifikowanej ścieżki dokumentu kontenera.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli dokument został pomyślnie zarejestrowany; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji podczas tworzenia lub otwierania nazwanego pliku, aby zarejestrować dokument z bibliotekami DLL systemu OLE. Nie ma potrzeby wywoływania tej funkcji, jeśli dokument reprezentuje element osadzony.

Jeśli używasz `COleTemplateServer` w aplikacji, `Register` jest wywoływana dla `OnNewDocument`Ciebie `OnOpenDocument`przez `OnSaveDocument` `COleLinkingDoc`implementacji , i .

## <a name="colelinkingdocrevoke"></a><a name="revoke"></a>COleLinkingDoc::Odwołaj

Informuje biblioteki DLL systemu OLE, że dokument nie jest już otwarty.

```cpp
void Revoke();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby odwołać rejestrację dokumentu z bibliotekami DLL systemu OLE.

Tę funkcję należy wywołać podczas zamykania nazwanego pliku, ale zwykle nie trzeba go wywoływać bezpośrednio. `Revoke`jest wymagane przez `COleLinkingDoc` `OnCloseDocument`wdrożenie `OnNewDocument`, , `OnOpenDocument`i `OnSaveDocument`.

## <a name="see-also"></a>Zobacz też

[Próbka MFC OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleDocument](../../mfc/reference/coledocument-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
