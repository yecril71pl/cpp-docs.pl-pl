---
title: Klasa COleStreamFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
dev_langs:
- C++
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efb042f87e10bec9fff53fcb1d22d56ed3c68ef3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="colestreamfile-class"></a>Klasa COleStreamFile
Reprezentuje strumienia danych ( `IStream`) w pliku złożonego jako część OLE magazynem strukturalnym.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleStreamFile : public CFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleStreamFile::COleStreamFile](#colestreamfile)|Konstruuje `COleStreamFile` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleStreamFile::Attach](#attach)|Kojarzy strumień z obiektu.|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Tworzy strumień z globalnej pamięci i kojarzy go z obiektem.|  
|[COleStreamFile::CreateStream](#createstream)|Tworzy strumień i kojarzy go z obiektem.|  
|[COleStreamFile::Detach](#detach)|Usuwa skojarzenia strumień z obiektu.|  
|[COleStreamFile::GetStream](#getstream)|Zwraca bieżący strumień.|  
|[COleStreamFile::OpenStream](#openstream)|Bezpiecznie otwiera strumienia i kojarzy go z obiektem.|  
  
## <a name="remarks"></a>Uwagi  
 `IStorage` Obiektu muszą istnieć przed strumienia można otworzyć lub utworzyć, chyba że jest strumienia pamięci.  
  
 `COleStreamFile`obiekty są dokładnie tak samo, jak manipulować [cfile —](../../mfc/reference/cfile-class.md) obiektów.  
  
 Aby uzyskać więcej informacji na temat manipulowanie strumieni i magazynów, zobacz artykuł [kontenery: pliki złożone](../../mfc/containers-compound-files.md)...  
  
 Aby uzyskać więcej informacji, zobacz [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) i [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="attach"></a>COleStreamFile::Attach  
 Kojarzy podany strumienia OLE z `COleStreamFile` obiektu.  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStream`  
 Wskazuje strumienia OLE ( `IStream`) ma zostać skojarzony z obiektem. Nie może być **NULL**.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt nie może już być skojarzone z strumienia OLE.  
  
 Aby uzyskać więcej informacji, zobacz [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) w zestawie Windows SDK.  
  
##  <a name="colestreamfile"></a>COleStreamFile::COleStreamFile  
 Tworzy `COleStreamFile` obiektu.  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStream`  
 Wskaźnik do strumienia OLE ma zostać skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `lpStream` jest **NULL**, obiekt nie jest skojarzony z strumienia OLE, w przeciwnym wypadku obiekt jest skojarzony z dostarczonego strumienia OLE.  
  
 Aby uzyskać więcej informacji, zobacz [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) w zestawie Windows SDK.  
  
##  <a name="creatememorystream"></a>COleStreamFile::CreateMemoryStream  
 Bezpiecznie tworzy strumień nowe za mało pamięci globalnej, udostępnionych awarii w przypadku normalnych, oczekiwany warunek.  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `pError`  
 Wskazuje [CFileException](../../mfc/reference/cfileexception-class.md) obiektu lub **NULL** wskazuje, że stan ukończenia operacji tworzenia. Podaj ten parametr, jeśli chcesz monitorować możliwych wyjątków generowanych przez próby utworzenia strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pamięć jest przydzielane przez podsystem OLE.  
  
 Aby uzyskać więcej informacji, zobacz [CreateStreamOnHGlobal](http://msdn.microsoft.com/library/windows/desktop/aa378980) w zestawie Windows SDK.  
  
##  <a name="createstream"></a>COleStreamFile::CreateStream  
 Bezpiecznie tworzy nowy strumień w obiekcie dostarczony magazynu, gdzie awarii jest to normalne, oczekiwane.  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStorage`  
 Wskazuje obiekt magazynu OLE, który zawiera strumienia, który ma zostać utworzony. Nie może być **NULL**.  
  
 `lpszStreamName`  
 Nazwa strumienia, który ma zostać utworzony. Nie może być **NULL**.  
  
 `nOpenFlags`  
 Tryb dostępu do używania podczas otwierania strumienia. Na wyłączność, odczytu/zapisu i tworzenia trybów używanych domyślnie. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Wskazuje [CFileException](../../mfc/reference/cfileexception-class.md) obiektu lub **NULL**. Podaj ten parametr, jeśli chcesz monitorować możliwych wyjątków generowanych przez próby utworzenia strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Plik zostanie wygenerowany wyjątek Jeśli Otwórz nie powiedzie się i `pError` nie jest **NULL**.  
  
 Aby uzyskać więcej informacji, zobacz [IStorage::CreateStream](http://msdn.microsoft.com/library/windows/desktop/aa380020) w zestawie Windows SDK.  
  
##  <a name="detach"></a>COleStreamFile::Detach  
 Usuwa skojarzenia strumień z obiektu bez zamykania strumienia.  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do strumienia ( `IStream`) który został skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Należy najpierw zamknąć strumienia w dowolny sposób innych, aby program zakończy.  
  
 Aby uzyskać więcej informacji, zobacz [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) w zestawie Windows SDK.  
  
##  <a name="getstream"></a>COleStreamFile::GetStream  
 Wywołanie tej funkcji do zwraca wskaźnik do bieżącego strumienia.  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego interfejsu strumienia ( [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034)).  
  
##  <a name="openstream"></a>COleStreamFile::OpenStream  
 Otwiera istniejący strumienia.  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `lpStorage`  
 Wskazuje obiekt magazynu OLE, który zawiera strumienia do otwarcia. Nie może być **NULL**.  
  
 `lpszStreamName`  
 Nazwa strumienia do otwarcia. Nie może być **NULL**.  
  
 `nOpenFlags`  
 Tryb dostępu do używania podczas otwierania strumienia. Wyłączny i trybów używanych domyślnie odczytu/zapisu. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 `pError`  
 Wskazuje [CFileException](../../mfc/reference/cfileexception-class.md) obiektu lub **NULL**. Podaj ten parametr, jeśli chcesz monitorować możliwych wyjątków generowanych przez próby otwarcia strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli strumień jest otwarty pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Plik zostanie wygenerowany wyjątek Jeśli Otwórz nie powiedzie się i `pError` nie jest **NULL**.  
  
 Aby uzyskać więcej informacji, zobacz [IStorage::OpenStream](http://msdn.microsoft.com/library/windows/desktop/aa380025) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Cfile — klasa](../../mfc/reference/cfile-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



