---
title: Klasa CD2DMesh | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
dev_langs:
- C++
helpviewer_keywords:
- CD2DMesh [MFC], CD2DMesh
- CD2DMesh [MFC], Attach
- CD2DMesh [MFC], Create
- CD2DMesh [MFC], Destroy
- CD2DMesh [MFC], Detach
- CD2DMesh [MFC], Get
- CD2DMesh [MFC], IsValid
- CD2DMesh [MFC], Open
- CD2DMesh [MFC], m_pMesh
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc5db59c16c10026bf411d640c864cf0107691cb
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36952238"
---
# <a name="cd2dmesh-class"></a>Klasa CD2DMesh
Otoka dla ID2D1Mesh.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CD2DMesh : public CD2DResource;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DMesh::CD2DMesh](#cd2dmesh)|Tworzy obiekt CD2DMesh.|  
|[CD2DMesh:: ~ CD2DMesh](#_dtorcd2dmesh)|Destruktor. Wywoływane, gdy trwa niszczenie obiektów D2D siatki.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DMesh::attach](#attach)|Dołącza istniejący interfejs zasobów do obiektu|  
|[CD2DMesh::Create](#create)|Tworzy CD2DMesh. (Przesłania [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DMesh::Destroy](#destroy)|Niszczy obiektu CD2DMesh. (Przesłania [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DMesh::detach](#detach)|Odłącza interfejsu zasobów z obiektu|  
|[CD2DMesh::Get](#get)|Zwraca interfejs ID2D1Mesh|  
|[CD2DMesh::IsValid](#isvalid)|Sprawdza poprawność zasobów (zastępuje [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DMesh::Open](#open)|Otwiera siatkę populacji.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DMesh::operator ID2D1Mesh *](#operator_id2d1mesh_star)|Zwraca interfejs ID2D1Mesh|  
  
### <a name="protected-data-members"></a>Dane chronione elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CD2DMesh::m_pMesh](#m_pmesh)|Wskaźnik do ID2D1Mesh.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DMesh`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxrendertarget.h  
  
##  <a name="_dtorcd2dmesh"></a>  CD2DMesh:: ~ CD2DMesh  
 Destruktor. Wywoływane, gdy trwa niszczenie obiektów D2D siatki.  
  
```  
virtual ~CD2DMesh();
```  
  
##  <a name="attach"></a>  CD2DMesh::attach  
 Dołącza istniejący interfejs zasobów do obiektu  
  
```  
void Attach(ID2D1Mesh* pResource);
```  
  
### <a name="parameters"></a>Parametry  
 *pResource*  
 Interfejs istniejącego zasobu. Nie może mieć wartości NULL  
  
##  <a name="cd2dmesh"></a>  CD2DMesh::CD2DMesh  
 Tworzy obiekt CD2DMesh.  
  
```  
CD2DMesh(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *pParentTarget*  
 Wskaźnik do obiektu docelowego renderowania.  
  
 *bAutoDestroy*  
 Wskazuje, że obiekt zostanie zniszczony przez właściciela (pParentTarget).  
  
##  <a name="create"></a>  CD2DMesh::Create  
 Tworzy CD2DMesh.  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>Parametry  
 *pRenderTarget*  
 Wskaźnik do obiektu docelowego renderowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda zakończy się powodzeniem, zwraca wartość S_OK. W przeciwnym wypadku zwraca kod błędu HRESULT.  
  
##  <a name="destroy"></a>  CD2DMesh::Destroy  
 Niszczy obiektu CD2DMesh.  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>  CD2DMesh::detach  
 Odłącza interfejsu zasobów z obiektu  
  
```  
ID2D1Mesh* Detach();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do zasobów odłączyć interfejs.  
  
##  <a name="get"></a>  CD2DMesh::Get  
 Zwraca interfejs ID2D1Mesh  
  
```  
ID2D1Mesh* Get();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Mesh lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
##  <a name="isvalid"></a>  CD2DMesh::IsValid  
 Sprawdzanie poprawności zasobów  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość TRUE, jeśli zasób jest nieprawidłowy; w przeciwnym razie wartość FALSE.  
  
##  <a name="m_pmesh"></a>  CD2DMesh::m_pMesh  
 Wskaźnik do ID2D1Mesh.  
  
```  
ID2D1Mesh* m_pMesh;  
```  
  
##  <a name="open"></a>  CD2DMesh::Open  
 Otwiera siatkę populacji.  
  
```  
ID2D1TessellationSink* Open();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do ID2D1TessellationSink służący do wypełniania siatki.  
  
##  <a name="operator_id2d1mesh_star"></a>  CD2DMesh::operator ID2D1Mesh *  
 Zwraca interfejs ID2D1Mesh  
  
```  
operator ID2D1Mesh*();
```   
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do interfejsu ID2D1Mesh lub wartość NULL, jeśli obiekt nie został jeszcze zainicjowany.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy](../../mfc/reference/mfc-classes.md)
