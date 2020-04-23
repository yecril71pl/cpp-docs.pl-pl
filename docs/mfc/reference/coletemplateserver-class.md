---
title: Klasa COleTemplateServer
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
ms.openlocfilehash: 561da5060aae3c938dc3e55d0310718a881c1a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753727"
---
# <a name="coletemplateserver-class"></a>Klasa COleTemplateServer

Używane do edycji wizualnej OLE serwerów, serwerów automatyzacji i kontenerów łączy (aplikacje obsługujące łącza do osadzania).

## <a name="syntax"></a>Składnia

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Konstruuje `COleTemplateServer` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Łączy szablon dokumentu z `COleObjectFactory` obiektem źródłowym.|
|[COleTemplateServer::Wyrejestrowanie](#unregister)|Wyrejestrowanie skojarzonego szablonu dokumentu.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Rejestruje typ dokumentu w rejestrze systemu OLE.|

## <a name="remarks"></a>Uwagi

Ta klasa jest pochodną klasy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); zwykle można użyć `COleTemplateServer` bezpośrednio, a nie wyprowadzając własną klasę. `COleTemplateServer`używa obiektu [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) do zarządzania dokumentami serwera. Użyj `COleTemplateServer` podczas implementowania pełnego serwera, czyli serwera, który można uruchomić jako aplikacja autonomiczna. Pełne serwery są zazwyczaj aplikacjami interfejsu wielu dokumentów (MDI), chociaż obsługiwane są aplikacje interfejsu pojedynczego dokumentu (SDI). Jeden `COleTemplateServer` obiekt jest potrzebny dla każdego typu dokumentu serwera, który obsługuje aplikacja; oznacza to, że jeśli aplikacja serwera obsługuje zarówno arkusze, `COleTemplateServer` jak i wykresy, musisz mieć dwa obiekty.

`COleTemplateServer`zastępuje funkcję `OnCreateInstance` elementu członkowskiego `COleObjectFactory`zdefiniowaną przez . Ta funkcja elementu członkowskiego jest wywoływana przez strukturę do tworzenia obiektu C++ odpowiedniego typu.

Aby uzyskać więcej informacji o serwerach, zobacz artykuł [Serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Cobject](../../mfc/reference/cobject-class.md)

[Ccmdtarget](../../mfc/reference/ccmdtarget-class.md)

[Coleobjectfactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer

Konstruuje `COleTemplateServer` obiekt.

```
COleTemplateServer();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać krótki opis użycia `COleTemplateServer` klasy, zobacz [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) omówienie klasy.

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate

Łączy szablon dokumentu wskazywalny przez *pDocTemplate* z podstawowym [obiektem COleObjectFactory.](../../mfc/reference/coleobjectfactory-class.md)

```cpp
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parametry

*Clsid*<br/>
Odwołanie do identyfikatora klasy OLE, którego żąda szablon.

*pDocTemplate*<br/>
Wskaźnik do szablonu dokumentu.

*bMultiInstance*<br/>
Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. Jeśli TRUE, wiele wystąpień aplikacji są uruchamiane dla każdego żądania, aby utworzyć obiekt.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ClsID klucz](/windows/win32/com/clsid-key-hklm) w windows SDK.

## <a name="coletemplateserverunregister"></a><a name="unregister"></a>COleTemplateServer::Wyrejestrowanie

Wyrejestrowanie skojarzonego szablonu dokumentu.

```
BOOL Unregister();
```

### <a name="return-value"></a>Wartość zwracana

PRAWDA, jeśli się powiedzie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

EnterRemarks ( EnterRemarks )

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a>COleTemplateServer::UpdateRegistry

Ładuje informacje o typie pliku z ciągu szablonu dokumentu i umieszcza te informacje w rejestrze systemu OLE.

```cpp
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*n Typ aplikacji*<br/>
Wartość z wyliczenia OLE_APPTYPE, która jest zdefiniowana w AFXDISP. H. Może mieć jedną z następujących wartości:

- OAT_INPLACE_SERVER Server ma pełny interfejs użytkownika serwera.

- OAT_SERVER Serwer obsługuje tylko osadzanie.

- OAT_CONTAINER Container obsługuje łącza do obiektów osadzonych.

- OAT_DISPATCH_OBJECT Object jest `IDispatch`w stanie.

- OAT_DOC_OBJECT_SERVER Serwer obsługuje zarówno osadzanie, jak i model składnika Obiekt dokumentu.

*rglpszRegister*<br/>
Lista wpisów, która jest zapisywana w rejestrze tylko wtedy, gdy nie istnieją żadne wpisy.

*rglpszOverwrite*<br/>
Lista wpisów, które są zapisywane w rejestrze, niezależnie od tego, czy istnieją poprzednie wpisy.

*Bregister*<br/>
Określa, czy klasa ma być zarejestrowana. Jeśli *bRegister* jest TRUE, klasa jest zarejestrowana w rejestrze systemowym. W przeciwnym razie wyrejestruje klasę.

### <a name="remarks"></a>Uwagi

Informacje rejestracyjne są ładowane za pomocą wywołania [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Pobrane podciągi to podciągi `regFileTypeId`identyfikowane przez indeksy `regFileTypeName`i `fileNewName`, jak opisano na stronach referencyjnych. `GetDocString`

Jeśli `regFileTypeId` podciąg jest pusty lub `GetDocString` jeśli wywołanie nie powiedzie się z jakiegokolwiek innego powodu, ta funkcja kończy się niepowodzeniem, a informacje o pliku nie są wprowadzane do rejestru.

Informacje w argumentach *rglpszRegister* i *rglpszOverwrite* jest zapisywany w rejestrze poprzez wywołanie [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). Informacje domyślne, które są rejestrowane, gdy dwa argumenty są NULL, jest odpowiedni dla większości aplikacji. Aby uzyskać informacje na temat struktury informacji `AfxOleRegisterServerClass`w tych argumentach, zobacz .

Aby uzyskać więcej informacji, zobacz [Implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Zobacz też

[Przykładowy HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
