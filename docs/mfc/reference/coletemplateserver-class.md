---
title: Klasa element COleTemplateServer
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
ms.openlocfilehash: 4a1997497f3bddb405b712b5534f76e577dabfa8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503093"
---
# <a name="coletemplateserver-class"></a>Klasa element COleTemplateServer

Używane na potrzeby edycji wizualnej OLE, serwerów automatyzacji i kontenerów linków (aplikacje obsługujące linki do osadzania).

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
|[Element COleTemplateServer:: ConnectTemplate](#connecttemplate)|Łączy szablon dokumentu z obiektem źródłowym `COleObjectFactory` .|
|[COleTemplateServer::Unregister](#unregister)|Wyrejestrowuje szablon skojarzonego dokumentu.|
|[Element COleTemplateServer:: operacja UpdateRegistry](#updateregistry)|Rejestruje typ dokumentu w rejestrze systemu OLE.|

## <a name="remarks"></a>Uwagi

Ta klasa pochodzi od klasy [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md); Zazwyczaj można używać `COleTemplateServer` bezpośrednio zamiast wyprowadzania własnej klasy. `COleTemplateServer`używa obiektu [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) do zarządzania dokumentami na serwerze. Używane `COleTemplateServer` podczas implementowania pełnego serwera, czyli serwera, który może być uruchamiany jako aplikacja autonomiczna. Pełne serwery to zazwyczaj aplikacje interfejsu wielu dokumentów (MDI), chociaż obsługiwane są aplikacje interfejsu pojedynczego dokumentu (SDI). Jeden `COleTemplateServer` obiekt jest wymagany dla każdego typu dokumentu serwera obsługiwanego przez aplikację. oznacza to, że jeśli aplikacja serwera obsługuje arkusze i wykresy, muszą istnieć dwa `COleTemplateServer` obiekty.

`COleTemplateServer`przesłania funkcję `COleObjectFactory`członkowską zdefiniowaną przez. `OnCreateInstance` Ta funkcja członkowska jest wywoływana przez platformę w celu C++ utworzenia obiektu odpowiedniego typu.

Aby uzyskać więcej informacji na temat serwerów, zobacz [artykuł serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Wymagania

**Nagłówek:** AFXDISP. h

##  <a name="coletemplateserver"></a>Element COleTemplateServer:: element COleTemplateServer

Konstruuje `COleTemplateServer` obiekt.

```
COleTemplateServer();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać krótki opis użycia `COleTemplateServer` klasy, zobacz Omówienie klasy [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) .

##  <a name="connecttemplate"></a>Element COleTemplateServer:: ConnectTemplate

Łączy szablon dokumentu wskazywany przez *pDocTemplate* do bazowego obiektu [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md) .

```
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parametry

*Identyfikator*<br/>
Odwołanie do identyfikatora klasy OLE, który żądanie szablonu.

*pDocTemplate*<br/>
Wskaźnik do szablonu dokumentu.

*bMultiInstance*<br/>
Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. W przypadku wartości TRUE dla każdego żądania utworzenia obiektu uruchamiane jest wiele wystąpień aplikacji.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [klucz CLSID](/windows/win32/com/clsid-key-hklm) w Windows SDK.

##  <a name="unregister"></a>Element COleTemplateServer:: Unregister

Wyrejestrowuje szablon skojarzonego dokumentu.

```
BOOL Unregister();
```

### <a name="return-value"></a>Wartość zwracana

Wartość TRUE, jeśli powodzenie; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

EnterRemarks

##  <a name="updateregistry"></a>Element COleTemplateServer:: operacja UpdateRegistry

Ładuje informacje o typie pliku z ciągu szablonu dokumentu i umieszcza je w rejestrze systemu OLE.

```
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parametry

*nAppType*<br/>
Wartość z wyliczenia OLE_APPTYPE, która jest zdefiniowana w AFXDISP. C. Może mieć jedną z następujących wartości:

- Serwer OAT_INPLACE_SERVER ma pełny interfejs użytkownika serwera.

- Serwer OAT_SERVER obsługuje tylko osadzanie.

- Kontener OAT_CONTAINER obsługuje linki do osadzonych obiektów.

- Obiekt `IDispatch`OAT_DISPATCH_OBJECT.

- Serwer OAT_DOC_OBJECT_SERVER obsługuje zarówno osadzanie, jak i model składnika obiektu dokumentu.

*rglpszRegister*<br/>
Lista wpisów, które są zapisywane w rejestrze tylko wtedy, gdy nie istnieją żadne wpisy.

*rglpszOverwrite*<br/>
Lista wpisów, które są zapisywane w rejestrze bez względu na to, czy istnieją poprzednie wpisy.

*bRegister*<br/>
Określa, czy Klasa ma być zarejestrowana. Jeśli *bRegister* ma wartość true, Klasa jest zarejestrowana w rejestrze systemowym. W przeciwnym razie wyrejestruje klasę.

### <a name="remarks"></a>Uwagi

Informacje o rejestracji są ładowane za pomocą wywołania [CDocTemplate:: GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Pobrane podciągi to `regFileTypeId`te identyfikowane przez indeksy, `regFileTypeName`i `fileNewName`, zgodnie z opisem na `GetDocString` stronach referencyjnych.

Jeśli podciąg jest pusty lub jeśli `GetDocString` wywołanie zakończy się niepowodzeniem z innego powodu, ta funkcja zakończy się niepowodzeniem, a informacje o pliku nie zostaną wprowadzone do rejestru. `regFileTypeId`

Informacje w argumentach *rglpszRegister* i *rglpszOverwrite* są zapisywane w rejestrze przez wywołanie do [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass). Informacje domyślne, które są rejestrowane, gdy dwa argumenty mają wartość NULL, są odpowiednie dla większości aplikacji. Aby uzyskać informacje na temat struktury informacji w tych argumentach, zobacz `AfxOleRegisterServerClass`.

Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu IDispatch](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Zobacz także

[Przykład HIERSVR MFC](../../overview/visual-cpp-samples.md)<br/>
[Klasa COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
