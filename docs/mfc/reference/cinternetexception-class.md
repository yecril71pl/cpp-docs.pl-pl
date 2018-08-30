---
title: Klasa CInternetException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
dev_langs:
- C++
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f1439fc2a5d49a775f55c7c25e45f4faa9b9c99f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211280"
---
# <a name="cinternetexception-class"></a>Klasa CInternetException
Przedstawia warunek wyjątku związany z operacją Internet.  
  
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
|[CInternetException::m_dwContext](#m_dwcontext)|Wartość kontekstu skojarzone z operacją, który spowodował wyjątek.|  
|[CInternetException::m_dwError](#m_dwerror)|Błąd, który spowodował wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 `CInternetException` Klasa zawiera dwa publiczne elementy członkowskie danych: jeden posiada skojarzony z wyjątkiem kod błędu:, a drugi zawiera identyfikator kontekstu w aplikacji internetowej skojarzony z błędem.  
  
 Aby uzyskać więcej informacji na temat identyfikatorów kontekstu dla aplikacji internetowych, zobacz artykuł [Internet programowanie za pomocą interfejsu WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CInternetException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxinet.h  
  
##  <a name="cinternetexception"></a>  CInternetException::CInternetException  
 Ta funkcja członkowska jest wywoływana, gdy `CInternetException` obiekt zostanie utworzony.  
  
```  
CInternetException(DWORD dwError);
```  
  
### <a name="parameters"></a>Parametry  
 *dwError*  
 Błąd, który spowodował wyjątek.  
  
### <a name="remarks"></a>Uwagi  
 Zgłoszenie CInternetException, wywołaj funkcję globalne MFC [afxthrowinternetexception —](internet-url-parsing-globals.md#afxthrowinternetexception).  
  
##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext  
 Wartość kontekstu skojarzone z operacji dotyczącej Internet.  
  
```  
DWORD_PTR m_dwContext;  
```  
  
### <a name="remarks"></a>Uwagi  
 W pierwotnie określono identyfikator kontekstu [CInternetSession](../../mfc/reference/cinternetsession-class.md) i przekazywany przez MFC, aby [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)— i [CInternetFile](../../mfc/reference/cinternetfile-class.md)-klas pochodnych. Możesz zastąpić to ustawienie domyślne i przypisać dowolny *dwContext* parametru wybranej wartości. *dwContext* jest skojarzony z wszelkich operacji danego obiektu. *dwContext* określa informacje o stanie operacji zwrócony przez [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
##  <a name="m_dwerror"></a>  CInternetException::m_dwError  
 Błąd, który spowodował wyjątek.  
  
```  
DWORD m_dwError;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ta wartość błędu może być systemem znaleziono w powiodło się. kod błędu. H, lub wartość błędu z WININET. H.  
  
 Aby uzyskać listę kodów błędów systemu Win32, zobacz [kody błędów](/windows/desktop/Debug/system-error-codes). Aby uzyskać listę komunikatów o błędach specyficzne dla Internetu Zobacz. Zarówno tematy znajdują się w zestawie Windows SDK.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CException](../../mfc/reference/cexception-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CException](../../mfc/reference/cexception-class.md)
