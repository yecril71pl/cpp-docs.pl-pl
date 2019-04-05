---
title: COleTemplateServer Class
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: 3abdf1dc2da5ef9a111371b501d5cd8ce208825d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "58781214"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer Class

Używany do edytowania serwerów, serwerów automatyzacji i kontenerów łączy (aplikacje, które obsługują linki do wbudowanych elementów) obrazu OLE.

## <a name="syntax"></a>Składnia

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Konstruuje `COleTemplateServer` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Nawiązanie połączenia z szablonu dokumentu bazowego `COleObjectFactory` obiektu.|
|[COleTemplateServer::Unregister](#unregister)|Wyrejestrowuje szablonu powiązanego dokumentu.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Rejestruje typ dokumentu z rejestru systemowego OLE.|

## <a name="remarks"></a>Uwagi

Ta klasa jest pochodną klasy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); zazwyczaj można użyć `COleTemplateServer` bezpośrednio, zamiast wyprowadzanie własne klasy. `COleTemplateServer` używa [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) obiektów do zarządzania dokumentami serwera. Użyj `COleTemplateServer` podczas implementowania całego serwera, oznacza to, że serwer, który może działać jako oddzielną aplikację. Pełne są to zazwyczaj wielu aplikacji interfejsu (MDI) dokumentu, aplikacje interfejsu (SDI) pojedynczego dokumentu są obsługiwane. Jeden `COleTemplateServer` obiektu jest wymagany w przypadku każdego typu dokumentu serwera aplikacji obsługuje; oznacza to, jeśli aplikacja serwera obsługuje zarówno arkuszy, jak i wykresy, musisz mieć dwa `COleTemplateServer` obiektów.

`COleTemplateServer` zastępuje `OnCreateInstance` funkcja elementu członkowskiego zdefiniowane przez `COleObjectFactory`. Ta funkcja członkowska jest wywoływana przez strukturę w celu utworzenia obiektu języka C++, właściwego typu.

Aby uzyskać więcej informacji na temat serwerów, zobacz artykuł [serwerów: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

##  <a name="coletemplateserver"></a>  COleTemplateServer::COleTemplateServer

Konstruuje `COleTemplateServer` obiektu.

```
COleTemplateServer();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać krótki opis korzystania z `COleTemplateServer` klasy, zobacz [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) klasa — Przegląd.

##  <a name="connecttemplate"></a>  COleTemplateServer::ConnectTemplate

Nawiązuje połączenie z szablonem dokumentu wskazywany przez *pDocTemplate* źródłowy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) obiektu.

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parametry

*Identyfikator klasy*<br/>
Odwołanie do Identyfikatora klasy OLE, który żąda szablonu.

*pDocTemplate*<br/>
Wskaźnik do szablonu dokumentu.

*bMultiInstance*<br/>
Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. W przypadku wartości TRUE dla każdego żądania utworzyć obiekt uruchomienia wielu wystąpień aplikacji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [klucz identyfikator CLSID](/windows/desktop/com/clsid-key-hklm) w zestawie Windows SDK.

##  <a name="unregister"></a>  COleTemplateServer::Unregister

Wyrejestrowuje szablonu powiązanego dokumentu.

```
BOOL Unregister();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli to się powiedzie; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

EnterRemarks

##  <a name="updateregistry"></a>  COleTemplateServer::UpdateRegistry

Ładuje informacje o typie pliku z parametrów szablonu dokumentu, a następnie umieszcza te informacje w rejestrze systemowym OLE.

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*nAppType*<br/>
Wartość wyliczenia OLE_APPTYPE, która jest zdefiniowana w AFXDISP. H. Może mieć jeden z następujących wartości:

- OAT_INPLACE_SERVER serwer ma interfejs użytkownika pełny serwer.

- OAT_SERVER Server obsługuje tylko osadzania.

- Kontener OAT_CONTAINER obsługuje łącza do osadzonych obiektów.

- Obiekt OAT_DISPATCH_OBJECT jest `IDispatch`-stanie.

- OAT_DOC_OBJECT_SERVER Server obsługuje zarówno osadzania i model obiektu dokumentu składnika.

*rglpszRegister*<br/>
Lista wpisy są zapisywane w rejestrze, tylko wtedy, gdy istnieje żadnych wpisów.

*rglpszOverwrite*<br/>
Lista wpisy są zapisywane w rejestrze, niezależnie od tego, czy istnieje żadnych poprzednich wpisów.

*bRegister*<br/>
Określa, czy klasa jest do zarejestrowania. Jeśli *bRegister* ma wartość PRAWDA, klasa jest rejestrowana z rejestru systemowego. W przeciwnym razie wyrejestrowuje klasy.

### <a name="remarks"></a>Uwagi

Informacje o rejestracji jest ładowany przez wywołanie [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Podciągi pobierane są identyfikowane za pomocą indeksy `regFileTypeId`, `regFileTypeName`, i `fileNewName`, zgodnie z opisem w `GetDocString` odwoływać się do strony.

Jeśli `regFileTypeId` podciągu jest puste lub jeśli wywołanie `GetDocString` kończy się niepowodzeniem dla jakiegokolwiek innego powodu, ta funkcja nie powiedzie się i informacje o pliku nie zostanie wprowadzona w rejestrze.

Informacje przedstawione w argumentach *rglpszRegister* i *rglpszOverwrite* są zapisywane w rejestrze za pomocą wywołania [afxoleregisterserverclass —](application-control.md#afxoleregisterserverclass). Domyślne informacje, który jest zarejestrowany, gdy dwa argumenty mają wartość NULL, jest odpowiedni dla większości aplikacji. Aby uzyskać informacji na temat struktury informacje zawarte w tych argumentów, zobacz `AfxOleRegisterServerClass`.

Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Zobacz także

[Próbki MFC HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[Coleobjectfactory — klasa](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Diagram hierarchii](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc Class](../../mfc/reference/coleserverdoc-class.md)<br/>
[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
