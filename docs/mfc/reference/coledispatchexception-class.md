---
title: Klasa COleDispatchException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
dev_langs: C++
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e25d83c2ae91424e80b07282bc5967a34745f412
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="coledispatchexception-class"></a>Klasa COleDispatchException
Obsługi wyjątków specyficzne dla OLE `IDispatch` interfejsu, który jest kluczowym elementem automatyzacji OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleDispatchException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleDispatchException::m_dwHelpContext](#m_dwhelpcontext)|Kontekst pomocy dla błędu.|  
|[COleDispatchException::m_strDescription](#m_strdescription)|Opis błędu ustne.|  
|[COleDispatchException::m_strHelpFile](#m_strhelpfile)|Plik do korzystania z pomocy `m_dwHelpContext`.|  
|[COleDispatchException::m_strSource](#m_strsource)|Aplikacji, która wygenerowała wyjątek.|  
|[COleDispatchException::m_wCode](#m_wcode)|`IDispatch`— Kod błędu.|  
  
## <a name="remarks"></a>Uwagi  
 Jak pochodną klasy wyjątków `CException` klasa, podstawowa `COleDispatchException` mogą być używane z **THROW**, `THROW_LAST`, **SPRÓBUJ**, **CATCH**, `AND_CATCH`, i `END_CATCH` makra.  
  
 Ogólnie rzecz biorąc, należy wywołać [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) do tworzenia i throw `COleDispatchException` obiektu.  
  
 Aby uzyskać więcej informacji dotyczących wyjątków, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `COleDispatchException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="m_dwhelpcontext"></a>COleDispatchException::m_dwHelpContext  
 Identyfikuje kontekst pomocy w aplikacji pomocy (. Plik HLP).  
  
```  
DWORD m_dwHelpContext;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski jest ustawiany przez funkcję [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) po jest zgłaszany wyjątek.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strdescription"></a>COleDispatchException::m_strDescription  
 Zawiera opis ustne błąd, na przykład "Dysk jest zapełniony."  
  
```  
CString m_strDescription;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski jest ustawiany przez funkcję [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) po jest zgłaszany wyjątek.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_strhelpfile"></a>COleDispatchException::m_strHelpFile  
 Platformę wypełnia tego ciągu o nazwie pliku pomocy w aplikacji.  
  
```  
CString m_strHelpFile;  
```  
  
##  <a name="m_strsource"></a>COleDispatchException::m_strSource  
 Platformę wypełnia tego ciągu o nazwie aplikacji, która wygenerowała wyjątek.  
  
```  
CString m_strSource;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
##  <a name="m_wcode"></a>COleDispatchException::m_wCode  
 Zawiera kod błędu specyficzne dla aplikacji.  
  
```  
WORD m_wCode;  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten element członkowski jest ustawiany przez funkcję [afxthrowoledispatchexception —](exception-processing.md#afxthrowoledispatchexception) po jest zgłaszany wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CALCDRIV](../../visual-cpp-samples.md)   
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)   
 [Klasa COleException](../../mfc/reference/coleexception-class.md)
