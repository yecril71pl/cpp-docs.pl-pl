---
title: Klasa CCachedDataPathProperty | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
dev_langs:
- C++
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2fb62a905d092a347103ea98fcd323e3778ed458
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ccacheddatapathproperty-class"></a>Klasa CCachedDataPathProperty
Implementuje OLE kontrolować właściwości przesyłane asynchronicznie, a w pliku pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CCachedDataPathProperty : public CDataPathProperty  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Konstruuje `CCachedDataPathProperty` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`obiekt, w którym do pamięci podręcznej danych.|  
  
## <a name="remarks"></a>Uwagi  
 Plik pamięci są przechowywane w pamięci RAM, a nie na dysku i jest przydatne w przypadku transferów fast tymczasowych.  
  
 Wraz z programem **CAysncMonikerFile** i `CDataPathProperty`, `CCachedDataPathProperty` zapewnia funkcje do użytku monikery asynchroniczne formantów OLE. Z `CCachedDataPathProperty` obiekty, są w stanie asynchronicznego przesyłania danych z pliku lub adres URL źródła i zapisz go w pliku pamięci za pomocą `m_Cache` zmiennej publicznej. Wszystkie dane są przechowywane w pliku pamięci i nie musi zastąpić [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) , chyba że chcesz obserwować powiadomienia i odpowiedzi. Na przykład w przypadku przenoszenia duży. Plik GIF, aby powiadomić formantu Odebrano większej ilości danych, a jego powinien automatyczne odświeżenie, należy zastąpić `OnDataAvailable` dotyczących powiadamiania.  
  
 Klasa `CCachedDataPathProperty` jest pochodną `CDataPathProperty`.  
  
 Aby uzyskać więcej informacji o sposobie używania monikery asynchroniczne i formantów w aplikacji internetowych zobacz następujące tematy:  
  
- [Internet pierwszych kroków: Formanty ActiveX](../../mfc/activex-controls-on-the-internet.md)  
  
- [Internet pierwszych kroków: Monikery asynchroniczne](../../mfc/asynchronous-monikers-on-the-internet.md)  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)  
  
 [CMonikerFile](../../mfc/reference/cmonikerfile-class.md)  
  
 [CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)  
  
 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)  
  
 `CCachedDataPathProperty`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxctl.h  
  
##  <a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty  
 Konstruuje `CCachedDataPathProperty` obiektu.  
  
```  
CCachedDataPathProperty(COleControl* pControl = NULL);

 
CCachedDataPathProperty(
    LPCTSTR lpszPath,  
    COleControl* pControl = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pControl`  
 Wskaźnik do obiektu formantu ActiveX ma zostać skojarzony z tym `CCachedDataPathProperty` obiektu.  
  
 `lpszPath`  
 Ścieżki, która może być bezwzględny lub względny, używany do tworzenia asynchroniczne krótkiej nazwy odwołujących się do rzeczywistej lokalizacji bezwzględnej właściwości. `CCachedDataPathProperty`używa adresów URL, a nie nazwy plików. Jeśli chcesz `CCachedDataPathProperty` obiektów do pliku, dołączenie wartości file:// do ścieżki.  
  
### <a name="remarks"></a>Uwagi  
 `COleControl` Obiekt wskazywany przez `pControl` jest używany przez [Otwórz](../../mfc/reference/cdatapathproperty-class.md#open) i pobrać klas pochodnych. Jeśli `pControl` jest **NULL**, kontrolki używane z **Otwórz** powinien być ustawiony z [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol). Jeśli `lpszPath` jest **NULL**, można przekazać w ścieżce za pośrednictwem **Otwórz** lub ustaw ją z [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath).  
  
##  <a name="m_cache"></a>CCachedDataPathProperty::m_Cache  
 Zawiera nazwę klasy w pliku pamięci, do którego dane są buforowane.  
  
```  
CMemFile m_Cache;  
```  
  
### <a name="remarks"></a>Uwagi  
 Plik pamięci są przechowywane w pamięci RAM, a nie na dysku.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)
