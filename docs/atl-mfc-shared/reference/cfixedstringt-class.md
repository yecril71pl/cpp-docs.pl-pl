---
title: Klasa CFixedStringT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs: C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f66749272649fe230b31e770a175e0b94441b90
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cfixedstringt-class"></a>Klasa CFixedStringT
Ta klasa reprezentuje obiekt ciągu z buforu, stały znaków.  
  
## <a name="syntax"></a>Składnia  
  
```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```  
  
#### <a name="parameters"></a>Parametry  
 `StringType`  
 Używane jako klasę podstawową dla obiekt stały ciąg i może być dowolną `CStringT`— na podstawie typu. Oto kilka przykładów `CString`, `CStringA`, i `CStringW`.  
  
 *t_nChars*  
 Liczba znaków przechowywanych w buforze.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFixedStringT::CFixedStringT](#cfixedstringt)|Konstruktor z obiektem ciągu.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CFixedStringT::operator =](#eq)|Przypisuje nową wartość do `CFixedStringT` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa jest przykład klasy niestandardowy ciąg na podstawie `CStringT`. Mimo że jest to bardzo podobne dwie klasy różnią się w implementacji. Główne różnice między `CFixedStringT` i `CStringT` są:  
  
-   Bufor początkowy znak jest przydzielona jako część obiektu i ma rozmiar *t_nChars*. Dzięki temu **CFixedString** obiektu zajmować fragmentu pamięci ciągłej względów wydajności. Jednak jeśli zawartość `CFixedStringT` obiektu przekroczy *t_nChars*, dynamicznie przydzielić buforu.  
  
-   Bufor znaków dla `CFixedStringT` obiektu jest zawsze taką samą długość ( *t_nChars*). Brak bez ograniczeń rozmiar buforu dla `CStringT` obiektów.  
  
-   Menedżer pamięci dla `CFixedStringT` jest dostosowana tak, aby udostępnianie [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) obiektu między co najmniej dwa `CFixedStringT` objectsis niedozwolone. `CStringT`obiekty nie mają tego ograniczenia.  
  
 Aby uzyskać więcej informacji na temat dostosowywania `CFixedStringT` i zarządzania pamięci dla obiektów typu string ogólnie rzecz biorąc, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlStringMgr`  
  
 `StringType`  
  
 `CFixedStringMgr`  
  
 `CFixedStringT`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cstringt.h  
  
##  <a name="cfixedstringt"></a>CFixedStringT::CFixedStringT  
 Konstruuje `CFixedStringT` obiektu.  
  
```
CFixedStringT() throw();
explicit CFixedStringT(IAtlStringMgr* pStringMgr) throw();
CFixedStringT(const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT(const StringType& str);
CFixedStringT(const StringType::XCHAR* psz);
explicit CFixedStringT(const StringType::YCHAR* psz);
explicit CFixedStringT(const unsigned char* psz);
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Ciąg zakończony zerem, ma zostać skopiowany do tego `CFixedStringT` obiektu.  
  
 `str`  
 Istniejące `CFixedStringT` obiekt ma zostać skopiowany do tego `CFixedStringT` obiektu.  
  
 `pStringMgr`  
 Wskaźnik do Menedżera pamięci `CFixedStringT` obiektu. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięci dla `CFixedStringT`, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ konstruktorów skopiować dane wejściowe do nowego magazynu przydzielonego, należy zwrócić uwagę pamięci może spowodować wyjątków. Należy pamiętać, niektóre z tych konstruktorów pełnienie funkcji konwersji.  
  
##  <a name="operator__eq"></a>CFixedStringT::operator =  
 Ponownie inicjuje istniejące `CFixedStringT` obiektu o nowych danych.  
  
```
CFixedStringT<StringType, t_nChars>& operator=(
  const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Ciąg zakończony zerem, ma zostać skopiowany do tego `CFixedStringT` obiektu.  
  
 `psz`  
 Istniejące `CFixedStringT` do skopiowania do tego `CFixedStringT` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Należy zwrócić uwagę pamięci, wyjątki zawsze, gdy używasz operator przypisania, ponieważ nowy magazyn jest często przydzielone do przechowywania powstałe w ten sposób `CFixedStringT` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CStringT](../../atl-mfc-shared/reference/cstringt-class.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)




