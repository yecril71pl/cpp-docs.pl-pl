---
title: "Cgopherfile — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
dev_langs: C++
helpviewer_keywords: CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 48c8da8fda2cd70676476532b3ed3646285f0782
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cgopherfile-class"></a>Cgopherfile — klasa
Udostępnia funkcje znajdowania i odczytywania plików na serwerze gopher.  
  
> [!NOTE]
>  Klasy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` i ich elementy członkowskie są przestarzałe, ponieważ nie działają na platformie Windows XP, ale będą one nadal działać na starszych platformach.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CGopherFile : public CInternetFile  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="protected-constructors"></a>Konstruktory chronione  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CGopherFile::CGopherFile](#cgopherfile)|Konstruuje `CGopherFile` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Usługa gopher nie zezwala użytkownikom można zapisać danych do pliku gopher, ponieważ ta usługa działa głównie jako interfejs opartemu na menu wyszukiwania informacji. `CGopherFile` Funkcje Członkowskie **zapisu**, `WriteString`, i `Flush` nie są zaimplementowane w przypadku `CGopherFile`. Wywoływanie funkcji `CGopherFile` obiekt zwraca [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md).  
  
 Aby dowiedzieć się więcej na temat `CGopherFile` współpracuje z innych klas MFC Internet, zapoznaj się z artykułem [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cfile —](../../mfc/reference/cfile-class.md)  
  
 [CStdioFile](../../mfc/reference/cstdiofile-class.md)  
  
 [CInternetFile](../../mfc/reference/cinternetfile-class.md)  
  
 `CGopherFile`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cgopherfile"></a>CGopherFile::CGopherFile  
 Ta funkcja elementu członkowskiego jest wywoływana w celu utworzenia `CGopherFile` obiektu.  
  
```  
CGopherFile(
    HINTERNET hFile,  
    CGopherLocator& refLocator,  
    CGopherConnection* pConnection);

 
CGopherFile(
    HINTERNET hFile,  
    HINTERNET hSession,  
    LPCTSTR pstrLocator,  
    DWORD dwLocLen,  
    DWORD_PTR dwContext);
```  
  
### <a name="parameters"></a>Parametry  
 `hFile`  
 Dojście do `HINTERNET` pliku.  
  
 `refLocator`  
 Odwołanie do [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) obiektu.  
  
 `pConnection`  
 Wskaźnik do [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) obiektu.  
  
 `hSession`  
 Dojście do bieżącej sesji Internet.  
  
 `pstrLocator`  
 Wskaźnik do ciągu używana do lokalizowania serwera gopher. Zobacz [sesji Gopher](https://msdn.microsoft.com/library/24wz8xze.aspx) Aby uzyskać więcej informacji na temat lokalizatorów gopher.  
  
 *dwLocLen*  
 Wartość typu DWORD zawierającą liczbę bajtów w `pstrLocator`.  
  
 `dwContext`  
 Wskaźnik do identyfikator kontekstu otwierany plik.  
  
### <a name="remarks"></a>Uwagi  
 Należy `CGopherFile` obiektu do odczytu z pliku podczas sesji gopher Internet.  
  
 Nigdy nie twórz `CGopherFile` obiekt bezpośrednio. Zamiast tego wywołać [CGopherConnection::OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile) można otworzyć pliku na serwerze gopher.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CInternetFile](../../mfc/reference/cinternetfile-class.md)   
 [Klasa CGopherLocator](../../mfc/reference/cgopherlocator-class.md)   
 [Klasa CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)   
 [Klasa CGopherConnection](../../mfc/reference/cgopherconnection-class.md)
