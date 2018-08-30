---
title: Klasa COleStreamFile | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ab7b12c26854903379da0b67f9f64e2158195587
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211131"
---
# <a name="colestreamfile-class"></a>Klasa COleStreamFile
Przedstawia strumień danych (`IStream`) w pliku złożonym w ramach magazynu strukturalnego OLE.  
  
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
|[COleStreamFile::Attach](#attach)|Kojarzy strumienia z obiektem.|  
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|Tworzy strumień z globalnej pamięci i kojarzy ją z obiektem.|  
|[COleStreamFile::CreateStream](#createstream)|Tworzy strumień i kojarzy ją z obiektem.|  
|[COleStreamFile::Detach](#detach)|Powoduje usunięcie strumienia z obiektu.|  
|[COleStreamFile::GetStream](#getstream)|Zwraca bieżący strumień.|  
|[COleStreamFile::OpenStream](#openstream)|Bezpiecznie otwiera strumienia i kojarzy ją z obiektem.|  
  
## <a name="remarks"></a>Uwagi  
 `IStorage` Obiektu, musi istnieć strumienia można otworzyć lub utworzyć, chyba że jest to strumień pamięci.  
  
 `COleStreamFile` obiekty są dokładnie takie jak zmieniane [CFile](../../mfc/reference/cfile-class.md) obiektów.  
  
 Aby uzyskać więcej informacji na temat manipulowanie strumieni i magazynów, zobacz artykuł [kontenery: pliki złożone](../../mfc/containers-compound-files.md)...  
  
 Aby uzyskać więcej informacji, zobacz [IStream](/windows/desktop/api/objidl/nn-objidl-istream) i [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage) w zestawie Windows SDK.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `COleStreamFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxole.h  
  
##  <a name="attach"></a>  COleStreamFile::Attach  
 Kojarzy podany strumienia OLE przy użyciu `COleStreamFile` obiektu.  
  
```  
void Attach(LPSTREAM lpStream);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStream*  
 Wskazuje strumienia OLE (`IStream`) ma zostać skojarzony z obiektem. Nie może mieć wartości NULL.  
  
### <a name="remarks"></a>Uwagi  
 Obiekt nie może już być skojarzone z strumień OLE.  
  
 Aby uzyskać więcej informacji, zobacz [IStream](/windows/desktop/api/objidl/nn-objidl-istream) w zestawie Windows SDK.  
  
##  <a name="colestreamfile"></a>  COleStreamFile::COleStreamFile  
 Tworzy `COleStreamFile` obiektu.  
  
```  
COleStreamFile(LPSTREAM lpStream = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStream*  
 Wskaźnik do strumienia OLE, który ma zostać skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli *lpStream* ma wartość NULL, obiekt nie jest skojarzony z usługą stream OLE, w przeciwnym razie, obiekt jest skojarzony z podanej strumienia OLE.  
  
 Aby uzyskać więcej informacji, zobacz [IStream](/windows/desktop/api/objidl/nn-objidl-istream) w zestawie Windows SDK.  
  
##  <a name="creatememorystream"></a>  COleStreamFile::CreateMemoryStream  
 Bezpiecznie tworzy nowy strumień za mało pamięci globalnej, udostępniony, gdzie błędu jest to normalne, oczekiwane.  
  
```  
BOOL CreateMemoryStream(CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *pError*  
 Wskazuje [CFileException](../../mfc/reference/cfileexception-class.md) obiekt lub wartość NULL, która wskazuje stan ukończenia operacji tworzenia. Należy podać ten parametr, jeśli chcesz monitorować możliwych wyjątków generowanych przez próby utworzenia strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pamięć została przydzielona przez podsystem OLE.  
  
 Aby uzyskać więcej informacji, zobacz [CreateStreamOnHGlobal](/windows/desktop/api/combaseapi/nf-combaseapi-createstreamonhglobal) w zestawie Windows SDK.  
  
##  <a name="createstream"></a>  COleStreamFile::CreateStream  
 Obiekt dostarczony magazynu, w której błędu jest to normalne, oczekiwane bezpiecznie tworzy nowy strumień.  
  
```  
BOOL CreateStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStorage*  
 Wskazuje obiekt magazynu OLE, który zawiera strumienia, który ma zostać utworzony. Nie może mieć wartości NULL.  
  
 *lpszStreamName*  
 Nazwa strumienia, który ma zostać utworzony. Nie może mieć wartości NULL.  
  
 *nOpenFlags*  
 Tryb dostępu do użycia podczas otwierania w strumieniu. Wyłączne, odczytu/zapisu i Utwórz tryby domyślnie są używane. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 *pError*  
 Wskazuje [CFileException](../../mfc/reference/cfileexception-class.md) obiekt lub wartość NULL. Należy podać ten parametr, jeśli chcesz monitorować możliwych wyjątków generowanych przez próby utworzenia strumienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli strumień został utworzony pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wyjątek plików zostanie zgłoszony, jeśli Otwórz kończy się niepowodzeniem i *pError* nie ma wartości NULL.  
  
 Aby uzyskać więcej informacji, zobacz [IStorage::CreateStream](/windows/desktop/api/objidl/nf-objidl-istorage-createstream) w zestawie Windows SDK.  
  
##  <a name="detach"></a>  COleStreamFile::Detach  
 Powoduje usunięcie strumienia z obiektu bez zamykania w strumieniu.  
  
```  
LPSTREAM Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do strumienia (`IStream`) skojarzony z obiektem.  
  
### <a name="remarks"></a>Uwagi  
 Strumień musi być zamknięty w dowolny sposób innych, zanim program zakończy.  
  
 Aby uzyskać więcej informacji, zobacz [IStream](/windows/desktop/api/objidl/nn-objidl-istream) w zestawie Windows SDK.  
  
##  <a name="getstream"></a>  COleStreamFile::GetStream  
 Wywołaj tę funkcję, aby zwrócić wskaźnik do bieżącego strumienia.  
  
```  
IStream* GetStream() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego interfejsu strumienia ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream)).  
  
##  <a name="openstream"></a>  COleStreamFile::OpenStream  
 Zostanie otwarty istniejącego strumienia.  
  
```  
BOOL OpenStream(
    LPSTORAGE lpStorage,  
    LPCTSTR lpszStreamName,  
    DWORD nOpenFlags = modeReadWrite|shareExclusive,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 *lpStorage*  
 Wskazuje obiekt magazynu OLE, który zawiera strumienia do otwarcia. Nie może mieć wartości NULL.  
  
 *lpszStreamName*  
 Nazwa strumienia do otwarcia. Nie może mieć wartości NULL.  
  
 *nOpenFlags*  
 Tryb dostępu do użycia podczas otwierania w strumieniu. Wyłączne/zapisu i odczytu trybów używanych domyślnie. Aby uzyskać pełną listę dostępnych trybów, zobacz [CFile::CFile](../../mfc/reference/cfile-class.md#cfile).  
  
 *pError*  
 Wskazuje [CFileException](../../mfc/reference/cfileexception-class.md) obiekt lub wartość NULL. Należy podać ten parametr, jeśli chcesz monitorować możliwych wyjątków generowanych przez próby otwarcia w strumieniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeżeli strumień jest otwarty pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Wyjątek plików zostanie zgłoszony, jeśli Otwórz kończy się niepowodzeniem i *pError* nie ma wartości NULL.  
  
 Aby uzyskać więcej informacji, zobacz [IStorage::OpenStream](/windows/desktop/api/objidl/nf-objidl-istorage-openstream) w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CFile](../../mfc/reference/cfile-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



