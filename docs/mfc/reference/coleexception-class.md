---
title: Klasa COleException | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
dev_langs: C++
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7e895e893c6032a8f8d7db0549f872c82cd0d9b5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="coleexception-class"></a>Klasa COleException
Reprezentuje warunku wyjątku związanych z operacją OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleException::Process](#process)|Wykonuje translację zgłoszony wyjątek do kodu powrotnego OLE.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleException::m_sc](#m_sc)|Zawiera kod stanu wskazujący przyczynę wyjątek.|  
  
## <a name="remarks"></a>Uwagi  
 `COleException` Klasa zawiera element członkowski danych publicznych, który zawiera kod stanu wskazujący z powodu wyjątku.  
  
 Ogólnie rzecz biorąc, nie należy tworzyć `COleException` obiekt bezpośrednio; zamiast tego należy wywołać [afxthrowoleexception —](exception-processing.md#afxthrowoleexception).  
  
 Aby uzyskać więcej informacji dotyczących wyjątków, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [Cexception —](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="m_sc"></a>COleException::m_sc  
 Ten element członkowski danych zawiera kod stanu OLE wskazujący przyczynę wyjątek.  
  
```  
SCODE m_sc;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość tej zmiennej jest ustawiana przez [afxthrowoleexception —](exception-processing.md#afxthrowoleexception).  
  
 Aby uzyskać więcej informacji na temat `SCODE`, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]  
  
##  <a name="process"></a>COleException::Process  
 Wywołanie **procesu** funkcji członkowskiej tłumaczenie zgłoszony wyjątek do kodu stanu OLE.  
  
```  
static SCODE PASCAL Process(const CException* pAnyException);
```  
  
### <a name="parameters"></a>Parametry  
 *pAnyException*  
 Wskaźnik do zgłoszony wyjątek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kod stanu OLE.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta funkcja jest **statycznych**.  
  
 Aby uzyskać więcej informacji na temat `SCODE`, zobacz [struktury COM kody błędów](http://msdn.microsoft.com/library/windows/desktop/ms690088) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC CALCDRIV](../../visual-cpp-samples.md)   
 [Cexception — klasa](../../mfc/reference/cexception-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



