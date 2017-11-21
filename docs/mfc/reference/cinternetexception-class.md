---
title: Klasa CInternetException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
dev_langs: C++
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 94f75200599c941dbe63a194e6a71d1693e1810e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cinternetexception-class"></a>Klasa CInternetException
Reprezentuje warunku wyjątku związanych z operacją Internet.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CInternetException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetException::CInternetException](#cinternetexception)|Konstruuje `CInternetException` obiektu.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CInternetException::m_dwContext](#m_dwcontext)|Wartość kontekstu skojarzona z operacji, który spowodował wyjątek.|  
|[CInternetException::m_dwError](#m_dwerror)|Błąd, który spowodował wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 `CInternetException` Klasa zawiera dwa elementy członkowskie danych publicznego: jeden zawiera kod błędu skojarzony z wyjątkiem, a drugi zawiera identyfikator kontekstu aplikacji internetowej skojarzone z powodu błędu.  
  
 Aby uzyskać więcej informacji o identyfikatorach kontekst dla aplikacji internetowych, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cinternetexception"></a>CInternetException::CInternetException  
 Ta funkcja członkowska jest wywoływane, gdy `CInternetException` tworzony jest obiekt.  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>Parametry  
 `dwError`  
 Błąd, który spowodował wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Aby zgłosić CInternetException, wywołaj funkcję globalne MFC [afxthrowinternetexception —](internet-url-parsing-globals.md#afxthrowinternetexception).  
  
##  <a name="m_dwcontext"></a>CInternetException::m_dwContext  
 Wartość kontekstu skojarzona z operacji dotyczącej Internet.  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>Uwagi  
 Identyfikator kontekstu pierwotnie została określona w [CInternetSession](../../mfc/reference/cinternetsession-class.md) i przekazywane przez MFC do [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- i [CInternetFile](../../mfc/reference/cinternetfile-class.md)-klas pochodnych. Można zastąpić to ustawienie domyślne i przypisać jedną `dwContext` wartość wybrane parametru. `dwContext`jest powiązany z żadnej operacji danego obiektu. `dwContext`Określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
##  <a name="m_dwerror"></a>CInternetException::m_dwError  
 Błąd, który spowodował wyjątek.  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość tego błędu może być to system znaleziono w powiodło się. kod błędu. H, lub wartość błędu z WININET. H.  
  
 Aby uzyskać listę kodów błędów systemu Win32, zobacz [kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms681381). Aby uzyskać listę komunikatów o błędach specyficznych dla Internetu Zobacz. Zarówno tematy znajdują się w zestawie SDK systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Cexception — klasa](../../mfc/reference/cexception-class.md)
