---
title: Klasa COleLinkingDoc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
dev_langs:
- C++
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe37e1a159fa0138c237b58ffbd622292dcba714
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369850"
---
# <a name="colelinkingdoc-class"></a>Klasa COleLinkingDoc
Klasa podstawowa dla kontenerami OLE, które obsługują łączenie z elementami osadzonych, które zawierają.  
  
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
|[COleLinkingDoc::Register](#register)|Rejestruje dokumentu OLE systemowej biblioteki dll.|  
|[COleLinkingDoc::Revoke](#revoke)|Wycofanie rejestracji dokumentu.|  
  
### <a name="protected-methods"></a>Metody chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|Wyszukuje określony element osadzony.|  
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|Wyszukuje określony element połączony.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacji kontenera, który obsługuje łączenie elementy osadzone nazywa się "kontener link". [OCLIENT](../../visual-cpp-samples.md) Przykładowa aplikacja jest przykładem kontenera łącza.  
  
 Gdy połączonego elementu źródła jest element osadzony w innym dokumencie, że zawiera dokument musi zostać załadowany w kolejności osadzonego elementu do edycji. Z tego powodu kontenera link musi mieć możliwość uruchomienia przez inną aplikację kontenera, gdy użytkownik chce edytować źródło połączonego elementu. Aplikacja musi także używać [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) klasy, dzięki czemu można tworzyć dokumenty, gdy uruchamiana programowo.  
  
 Aby z kontenera kontenera łącza, pochodzi z klasy dokumentu `COleLinkingDoc` zamiast [COleDocument](../../mfc/reference/coledocument-class.md). Podobnie jak w przypadku innych kontener OLE, należy zaprojektować klasy do przechowywania aplikacji natywnej jak i elementy osadzone i połączone. Ponadto należy projektować struktur danych do przechowywania danych natywnych. W przypadku definiowania `CDocItem`-pochodnej klasy podczas aplikacji natywnych danych, można użyć interfejsu zdefiniowane przez `COleDocument` do przechowywania danych natywnego, a także danych OLE.  
  
 Aby zezwolić aplikacji na jej uruchomienie programowo przy użyciu innego kontenera, należy zadeklarować `COleTemplateServer` obiektu jako członek aplikacji `CWinApp`-klasy:  
  
 [!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]  
  
 W `InitInstance` funkcji członkowskiej klasy z `CWinApp`-klasy, tworzenie szablonu dokumentu i określ Twojej `COleLinkingDoc`-klasy jako klasa dokumentu:  
  
 [!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]  
  
 Połącz z `COleTemplateServer` obiektu do szablonów dokumentu przez wywołanie obiektu `ConnectTemplate` funkcji członkowskiej i klasy wszystkie obiekty w systemie OLE przez wywołanie metody register **COleTemplateServer::RegisterAll**:  
  
 [!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]  
  
 Przykładowe `CWinApp`-definicji klasy pochodnej i `InitInstance` funkcji, zobacz OCLIENT. H i OCLIENT. CPP w przykładowym MFC [OCLIENT](../../visual-cpp-samples.md).  
  
 Aby uzyskać więcej informacji na temat używania `COleLinkingDoc`, zobacz artykuły [kontenery: Implementowanie kontenera](../../mfc/containers-implementing-a-container.md) i [kontenery: funkcje zaawansowane](../../mfc/containers-advanced-features.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 `COleLinkingDoc`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc  
 Konstruuje `COleLinkingDoc` obiektu bez komunikacji z systemem OLE biblioteki dll.  
  
```  
COleLinkingDoc();
```  
  
### <a name="remarks"></a>Uwagi  
 Należy wywołać `Register` funkcji członkowskiej informują OLE o tym, że dokument jest otwarty.  
  
##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem  
 Wywoływane przez platformę, by określić czy dokument zawiera element osadzony OLE o określonej nazwie.  
  
```  
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItemName`  
 Wskaźnik do nazwy osadzonych obiektów OLE żądanego elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do określonego elementu; **NULL** Jeśli element nie zostanie znaleziony.  
  
### <a name="remarks"></a>Uwagi  
 Domyślna implementacja wyszukuje na liście elementów osadzonych dla elementu o określonej nazwie (porównanie nazwie jest rozróżniana wielkość liter). Jeśli masz własnej metody przechowywania lub nazewnictwa elementy osadzone OLE, należy przesłonić tę funkcję.  
  
##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem  
 Wywoływane przez platformę, by sprawdzić, czy dokument zawiera element połączonego serwera o określonej nazwie.  
  
```  
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Parametry  
 `lpszItemName`  
 Wskaźnik do nazwy połączonej OLE żądanego elementu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do określonego elementu; **NULL** Jeśli element nie zostanie znaleziony.  
  
### <a name="remarks"></a>Uwagi  
 Wartość domyślna `COleLinkingDoc` zawsze implementacja zwraca **NULL**. Ta funkcja jest przesłonięta w klasie pochodnej `COleServerDoc` wyszukiwania na liście elementów serwera OLE połączonego elementu o określonej nazwie (porównanie nazwie jest rozróżniana wielkość liter). Należy przesłonić tę funkcję, jeśli zaimplementowano metodę przechowywanie i pobieranie elementów połączonego serwera.  
  
##  <a name="register"></a>  COleLinkingDoc::Register  
 Informuje OLE systemowej biblioteki dll, że dokument jest otwarty.  
  
```  
BOOL Register(
    COleObjectFactory* pFactory,  
    LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parametry  
 *pFactory*  
 Wskaźnik do obiektu fabryki (może być **NULL**).  
  
 `lpszPathName`  
 Wskaźnik do dokumentu kontenera pełną ścieżkę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli dokument zostanie pomyślnie zarejestrowana; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, podczas tworzenia lub otwierania wskazanego pliku, aby zarejestrować dokument w systemie OLE biblioteki dll. Nie istnieje potrzeba do wywołania tej funkcji, jeśli dokument reprezentuje element osadzony.  
  
 Jeśli używasz `COleTemplateServer` w aplikacji, `Register` jest wywoływana przez `COleLinkingDoc`w implementacji `OnNewDocument`, `OnOpenDocument`, i `OnSaveDocument`.  
  
##  <a name="revoke"></a>  COleLinkingDoc::Revoke  
 Informuje OLE systemowej biblioteki dll, że dokumentu nie jest już otwarty.  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby odwołać dokumentu rejestracji w systemie OLE biblioteki dll.  
  
 Podczas zamykania pliku o nazwie powinny wywoływać tej funkcji, ale zwykle nie trzeba go wywołać bezpośrednio. `Revoke` jest wywoływana przez `COleLinkingDoc`w implementacji `OnCloseDocument`, `OnNewDocument`, `OnOpenDocument`, i `OnSaveDocument`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC OCLIENT](../../visual-cpp-samples.md)   
 [Klasa COleDocument](../../mfc/reference/coledocument-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDocTemplate](../../mfc/reference/cdoctemplate-class.md)
