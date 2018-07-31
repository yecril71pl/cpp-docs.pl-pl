---
title: Klasa CBookmark | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
dev_langs:
- C++
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9bd662c827650112d0e9bcf1d59086f4205aea58
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337621"
---
# <a name="cbookmark-class"></a>Klasa CBookmark
Przechowuje wartość zakładki w jego buforu.  
  
## <a name="syntax"></a>Składnia

```cpp
template < DBLENGTH nSize = 0 >  
class CBookmark : public CBookmarkBase
  
template <>  
class CBookmark< 0 > : public CBookmarkBase  
```  
  
### <a name="parameters"></a>Parametry  
 *nSize*  
 Rozmiar buforu zakładki w bajtach. Gdy *nSize* wynosi zero, bufor zakładki zostanie dynamicznie utworzony w czasie wykonywania.  

## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CBookmark](#cbookmark)|Konstruktor|  
|[Getbuffer —](#getbuffer)|Pobiera wskaźnik do buforu.|  
|[GetSize](#getsize)|Pobiera rozmiar buforu w bajtach.|  
|[SetBookmark](#setbookmark)|Ustawia wartość zakładki.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#operator)|Przypisuje jeden `CBookmark` klasy do innego.|  
  
## <a name="remarks"></a>Uwagi  
 `CBookmark<0>` jest specjalizacją szablonu `CBookmark`; buforu jest tworzone dynamicznie w czasie wykonywania.  

## <a name="cbookmark"></a> CBookmark::CBookmark
Konstruktor.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CBookmark();
   
CBookmark(DBLENGTH nSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 *nSize*  
 [in] Rozmiar buforu zakładki w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza funkcja ustawia bufor o wartości NULL i rozmiar buforu na 0. Druga funkcja ustawia rozmiar buforu *nSize*, a bufor tablicy bajtów *nSize* bajtów.  
  
> [!NOTE]
>  Ta funkcja jest dostępna tylko w `CBookmark<0>`. 
  
## <a name="getbuffer"></a> CBookmark::GetBuffer
Pobiera wskaźnik do buforu zakładki.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
virtual BYTE* GetBuffer() const throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do buforu zakładki. 

## <a name="getsize"></a> CBookmark::GetSize
Pobiera rozmiar buforu zakładki.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
virtual DBLENGTH GetSize() const throw();  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar buforu w bajtach.  

## <a name="setbookmark"></a> CBookmark::SetBookmark
Kopiuje wartość zakładki odwołuje się *pBuffer* do `CBookmark` buffer i ustawia rozmiar buforu *nSize*.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *nSize*  
 [in] Rozmiar buforu zakładki.  
  
 *pBuffer*  
 [in] Wskaźnik do tablicy typu byte, zawierającego wartość zakładki.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standardowa HRESULT.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest dostępna tylko w `CBookmark<0>`. 

## <a name="operator"></a> CBookmark::operator =
Przypisuje `CBookmark` obiektu do drugiego.  
  
### <a name="syntax"></a>Składnia  
  
```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();  
```  
  
### <a name="remarks"></a>Uwagi  
 Ten operator jest wymagana tylko w `CBookmark<0>`.   

## <a name="see-also"></a>Zobacz też  
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Szablony konsumentów OLE DB — dokumentacja](../../data/oledb/ole-db-consumer-templates-reference.md)