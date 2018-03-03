---
title: Klasa COleTemplateServer | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
dev_langs:
- C++
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4bf5f696eeff3e4e26a9d77714c0d5a6f093aaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coletemplateserver-class"></a>Klasa COleTemplateServer
Używany dla OLE visual edycji serwery, serwery automatyzacji i łącze kontenery (aplikacje, które obsługują łącza do osadzonego).  
  
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
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Łączy szablonu dokumentu do odpowiadającego `COleObjectFactory` obiektu.|  
|[COleTemplateServer::Unregister](#unregister)|Wyrejestrowuje szablonu skojarzonego dokumentu.|  
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Rejestruje typ dokumentu z rejestru systemowego OLE.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa pochodzi od klasy [coleobjectfactory —](../../mfc/reference/coleobjectfactory-class.md); zazwyczaj można użyć `COleTemplateServer` bezpośrednio zamiast wyprowadzanie własne klasy. `COleTemplateServer`używa [cdoctemplate —](../../mfc/reference/cdoctemplate-class.md) obiektu Zarządzanie dokumentami serwera. Użyj `COleTemplateServer` podczas implementowania całego serwera, oznacza to, że serwer, który może działać jako aplikacja autonomiczna. Pełne są to zazwyczaj wiele aplikacji interfejsu (MDI) dokumentu pojedynczego dokumentu (SDI) interfejsu aplikacji są obsługiwane. Jeden `COleTemplateServer` dla każdego typu dokumentu serwera aplikacji obsługuje wymagany jest obiekt; oznacza to, że jeśli aplikacja serwera obsługuje arkuszy i wykresy, użytkownik musi mieć dwa `COleTemplateServer` obiektów.  
  
 `COleTemplateServer`zastępuje `OnCreateInstance` funkcji członkowskich zdefiniowanych przez `COleObjectFactory`. Ta funkcja elementu członkowskiego jest wywoływana przez platformę, by utworzyć prawidłowego typu obiektu języka C++.  
  
 Aby uzyskać więcej informacji na temat serwerów, zobacz artykuł [serwery: Implementowanie serwera](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget —](../../mfc/reference/ccmdtarget-class.md)  
  
 [Coleobjectfactory —](../../mfc/reference/coleobjectfactory-class.md)  
  
 `COleTemplateServer`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer  
 Konstruuje `COleTemplateServer` obiektu.  
  
```  
COleTemplateServer();
```  
  
### <a name="remarks"></a>Uwagi  
 Krótki opis stosowania `COleTemplateServer` , zobacz [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md) Przegląd klasy.  
  
##  <a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate  
 Łączy szablonu dokumentu wskazywana przez `pDocTemplate` do odpowiadającego [coleobjectfactory —](../../mfc/reference/coleobjectfactory-class.md) obiektu.  
  
```  
void ConnectTemplate(
    REFCLSID clsid,  
    CDocTemplate* pDocTemplate,  
    BOOL bMultiInstance);
```  
  
### <a name="parameters"></a>Parametry  
 `clsid`  
 Odwołanie do Identyfikatora klasy OLE żąda szablonu.  
  
 `pDocTemplate`  
 Wskaźnik do szablonu dokumentu.  
  
 `bMultiInstance`  
 Wskazuje, czy pojedyncze wystąpienie aplikacji może obsługiwać wiele wystąpień. Jeśli **TRUE**, wiele wystąpień aplikacji będą uruchamiane dla każdego żądania do utworzenia obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [klucz CLSID](http://msdn.microsoft.com/library/windows/desktop/ms691424) w zestawie Windows SDK.  
  
##  <a name="unregister"></a>COleTemplateServer::Unregister  
 Wyrejestrowuje szablonu skojarzonego dokumentu.  
  
```  
BOOL Unregister();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli pomyślnie; w przeciwnym razie wartość FALSE.  
  
### <a name="remarks"></a>Uwagi  
 EnterRemarks  
  
##  <a name="updateregistry"></a>COleTemplateServer::UpdateRegistry  
 Ładuje informacje typu pliku z ciągu szablonu dokumentu i umieszcza te informacje w rejestrze systemu OLE.  
  
```  
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,  
    LPCTSTR* rglpszRegister = NULL,  
    LPCTSTR* rglpszOverwrite = NULL,  
    BOOL bRegister = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `nAppType`  
 Wartość z zakresu od **OLE_APPTYPE** wyliczenia, która jest zdefiniowana w AFXDISP. H. Może mieć jeden z następujących wartości:  
  
- `OAT_INPLACE_SERVER`Serwer ma interfejs użytkownika całego serwera.  
  
- `OAT_SERVER`Serwer obsługuje tylko osadzania.  
  
- `OAT_CONTAINER`Kontener obsługuje łącza do osadzonych obiektów.  
  
- `OAT_DISPATCH_OBJECT`Obiekt jest `IDispatch`-stanie.  
  
- **OAT_DOC_OBJECT_SERVER** Server obsługuje zarówno osadzanie i składnik modelu obiektu dokumentu.  
  
 `rglpszRegister`  
 Lista wpisy są zapisywane w rejestrze tylko wtedy, gdy istnieje żadnych wpisów.  
  
 `rglpszOverwrite`  
 Lista wpisy w rejestrze niezależnie od tego, czy istnieją wszystkie poprzednie wpisy są zapisywane.  
  
 `bRegister`  
 Określa, czy klasa jest rejestrowana. Jeśli `bRegister` jest **TRUE**, klasa został zarejestrowany za pomocą rejestru systemu. W przeciwnym razie go wyrejestrowuje klasy.  
  
### <a name="remarks"></a>Uwagi  
 Informacje o rejestracji jest ładowany za pomocą wywołania [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring). Podciągi pobierane są identyfikowane przez indeksy **regFileTypeId**, **regFileTypeName**, i **fileNewName**, zgodnie z opisem w `GetDocString` Odwołanie do strony.  
  
 Jeśli **regFileTypeId** podciąg jest pusty lub jeśli wywołanie `GetDocString` kończy się niepowodzeniem dla innego powodu, ta funkcja nie powiedzie się, a informacje o pliku nie została wprowadzona w rejestrze.  
  
 Informacje w argumentach `rglpszRegister` i `rglpszOverwrite` są zapisywane w rejestrze poprzez wywołanie [afxoleregisterserverclass —](application-control.md#afxoleregisterserverclass). Domyślne informacje, który jest zarejestrowany, gdy są dwa argumenty **NULL**, jest odpowiedni dla większości aplikacji. Aby uzyskać informacje na temat struktury informacji z tych argumentów, zobacz `AfxOleRegisterServerClass`.  
  
 Aby uzyskać więcej informacji, zobacz [implementowania interfejsu IDispatch](http://msdn.microsoft.com/en-us/0e171f7f-0022-4e9b-ac8e-98192828e945).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC HIERSVR](../../visual-cpp-samples.md)   
 [Coleobjectfactory — klasa](../../mfc/reference/coleobjectfactory-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleServerDoc](../../mfc/reference/coleserverdoc-class.md)   
 [Klasa COleServerItem](../../mfc/reference/coleserveritem-class.md)
