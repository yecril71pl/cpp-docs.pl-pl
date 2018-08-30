---
title: Klasa COleException | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
dev_langs:
- C++
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a472de31695ab6038cab9ba0158580f3d305194
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212491"
---
# <a name="coleexception-class"></a>Klasa COleException
Przedstawia warunek wyjątku związany z operacją OLE.  
  
## <a name="syntax"></a>Składnia  
  
```  
class COleException : public CException  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleException::Process](#process)|Wykonuje translację przechwycony wyjątek do zwróciło kod powrotny OLE.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[COleException::m_sc](#m_sc)|Zawiera kod stanu, która wskazuje przyczynę wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 `COleException` Klasa zawiera element członkowski danych publicznego, który zawiera kod stanu wskazujący przyczynę, dla wyjątku.  
  
 Ogólnie rzecz biorąc, nie należy tworzyć `COleException` obiektu bezpośrednio; zamiast tego należy wywołać [afxthrowoleexception —](exception-processing.md#afxthrowoleexception).  
  
 Aby uzyskać więcej informacji na temat wyjątków, zobacz artykuły [obsługi wyjątków (MFC)](../../mfc/exception-handling-in-mfc.md) i [wyjątki: wyjątki OLE](../../mfc/exceptions-ole-exceptions.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `COleException`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxdisp.h  
  
##  <a name="m_sc"></a>  COleException::m_sc  
 Ten element członkowski danych przechowuje kod stanu OLE, która wskazuje przyczynę wyjątku.  
  
```  
SCODE m_sc;  
```  
  
### <a name="remarks"></a>Uwagi  
 Wartość tej zmiennej jest ustawiana przez [afxthrowoleexception —](exception-processing.md#afxthrowoleexception).  
  
 Aby uzyskać więcej informacji na temat SCODE, zobacz [struktury COM kody błędów](/windows/desktop/com/structure-of-com-error-codes) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]  
  
##  <a name="process"></a>  COleException::Process  
 Wywołaj **procesu** funkcja elementu członkowskiego do translacji zgłoszony wyjątek, kod stanu OLE.  
  
```  
static SCODE PASCAL Process(const CException* pAnyException);
```  
  
### <a name="parameters"></a>Parametry  
 *pAnyException*  
 Wskaźnik do przechwyconego wyjątku.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kod stanu OLE.  
  
### <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta funkcja jest **statyczne**.  
  
 Aby uzyskać więcej informacji na temat SCODE, zobacz [struktury COM kody błędów](/windows/desktop/com/structure-of-com-error-codes) w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch).  
  
## <a name="see-also"></a>Zobacz też  
 [Próbki MFC CALCDRIV](../../visual-cpp-samples.md)   
 [Klasa CException](../../mfc/reference/cexception-class.md)   
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



