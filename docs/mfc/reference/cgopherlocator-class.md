---
title: Klasa CGopherLocator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
dev_langs:
- C++
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f466864e694f332f70d9f5932a528917a000974
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37041289"
---
# <a name="cgopherlocator-class"></a>Klasa CGopherLocator
Pobiera gopher "lokalizatora" z serwera gopher, określa typ lokalizatora i udostępnia Lokalizator [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md).  
  
> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementy członkowskie są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działać na starszych platformach.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CGopherLocator : public CObject  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherLocator::CGopherLocator](#cgopherlocator)|Konstruuje `CGopherLocator` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherLocator::GetLocatorType](#getlocatortype)|Analizuje lokalizatora gopher i określa jego atrybuty.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherLocator::operator LPCTSTR](#operator_lpctstr)|Bezpośredni dostęp do znaków przechowywanych w `CGopherLocator` obiekt jako ciąg w stylu języka C.|  
  
## <a name="remarks"></a>Uwagi  
 Aplikacji, musisz uzyskać lokalizatora serwer gopher, aby możliwe było pobieranie informacji z tego serwera. Gdy ma ona Lokalizator, to traktowane Lokalizator jako nieprzezroczyste token.  
  
 Każdy Lokalizator gopher ma atrybuty, które określają typ pliku lub znaleziono serwera. Zobacz [GetLocatorType](#getlocatortype) listę typy lokalizatorów gopher.  
  
 Zwykle aplikacja używa Lokalizator dla wywołania [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) do pobrania konkretnych danych.  
  
 Aby dowiedzieć się więcej na temat `CGopherLocator` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGopherLocator`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cgopherlocator"></a>  CGopherLocator::CGopherLocator  
 Ta funkcja członkowska jest wywoływana w celu utworzenia `CGopherLocator` obiektu.  
  
```  
CGopherLocator(const CGopherLocator& ref);
```  
  
### <a name="parameters"></a>Parametry  
 *ref*  
 Odwołanie do stałej `CGopherLocator` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Nigdy nie twórz `CGopherLocator` obiekt bezpośrednio. Zamiast tego wywołać [CGopherConnection::CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) do tworzenia i zwraca wskaźnik do `CGopherLocator` obiektu.  
  
##  <a name="getlocatortype"></a>  CGopherLocator::GetLocatorType  
 Wywołanie tej funkcji Członkowskich wybrany typ lokalizatora.  
  
```  
BOOL GetLocatorType(DWORD& dwRef) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *dwRef*  
 Odwołanie do `DWORD` który otrzyma Typ lokalizatora. Zobacz **uwagi** dla tabeli typów lokalizatora.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0. W przypadku niepowodzenia wywołania funkcji Win32 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) może zostać wywołana w celu ustalenia przyczyny błędu.  
  
### <a name="remarks"></a>Uwagi  
 Typy możliwe są następujące:  
  
|Wartość|Znaczenie|  
|-----------|-------------|  
|GOPHER_TYPE_TEXT_FILE|Plik tekstowy ASCII.|  
|GOPHER_TYPE_DIRECTORY|Katalog dodatkowe elementy Gopher.|  
|GOPHER_TYPE_CSO|Serwer CSO książki telefonicznej.|  
|GOPHER_TYPE_ERROR|Wskazuje na błąd.|  
|GOPHER_TYPE_MAC_BINHEX|Macintosh pliku w formacie BINHEX.|  
|GOPHER_TYPE_DOS_ARCHIVE|Plik archiwum DOS.|  
|GOPHER_TYPE_UNIX_UUENCODED|Plik UUENCODED.|  
|GOPHER_TYPE_INDEX_SERVER|Serwer indeksu.|  
|GOPHER_TYPE_TELNET|Serwer Telnet.|  
|GOPHER_TYPE_BINARY|Plik binarny.|  
|GOPHER_TYPE_REDUNDANT|Zduplikowany serwer. Informacje zawarte w jest duplikatem serwera podstawowego. Serwer główny jest ostatni wpis katalogu, który nie ma typu GOPHER_TYPE_REDUNDANT.|  
|GOPHER_TYPE_TN3270|Serwer TN3270.|  
|GOPHER_TYPE_GIF|Plik GIF grafiki.|  
|GOPHER_TYPE_IMAGE|Plik obrazu.|  
|GOPHER_TYPE_BITMAP|Plik mapy bitowej.|  
|GOPHER_TYPE_MOVIE|Filmu.|  
|GOPHER_TYPE_SOUND|Plik dźwiękowy.|  
|GOPHER_TYPE_HTML|Dokument HTML.|  
|GOPHER_TYPE_PDF|Plik PDF.|  
|GOPHER_TYPE_CALENDAR|Plik kalendarza.|  
|GOPHER_TYPE_INLINE|Wbudowany plik.|  
|GOPHER_TYPE_UNKNOWN|Typ elementu jest nieznany.|  
|GOPHER_TYPE_ASK|Poproś + elementu.|  
|GOPHER_TYPE_GOPHER_PLUS|Gopher + element.|  
  
##  <a name="operator_lpctstr"></a>  CGopherLocator::operator LPCTSTR  
 Ten operator rzutowania przydatne zapewnia efektywną metodę dostępu zawarte w ciągu C zerem `CGopherLocator` obiektu.  
  
```  
operator LPCTSTR () const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Znak wskaźnikiem do danych ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Żadne znaki nie są kopiowane; zwracany jest tylko wskaźnik.  
  
## <a name="see-also"></a>Zobacz też  
 [CObject — klasa](../../mfc/reference/cobject-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)
