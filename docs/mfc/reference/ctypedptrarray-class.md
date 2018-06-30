---
title: Ctypedptrarray — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTypedPtrArray
- AFXTEMPL/CTypedPtrArray
- AFXTEMPL/CTypedPtrArray::Add
- AFXTEMPL/CTypedPtrArray::Append
- AFXTEMPL/CTypedPtrArray::Copy
- AFXTEMPL/CTypedPtrArray::ElementAt
- AFXTEMPL/CTypedPtrArray::GetAt
- AFXTEMPL/CTypedPtrArray::InsertAt
- AFXTEMPL/CTypedPtrArray::SetAt
- AFXTEMPL/CTypedPtrArray::SetAtGrow
dev_langs:
- C++
helpviewer_keywords:
- CTypedPtrArray [MFC], Add
- CTypedPtrArray [MFC], Append
- CTypedPtrArray [MFC], Copy
- CTypedPtrArray [MFC], ElementAt
- CTypedPtrArray [MFC], GetAt
- CTypedPtrArray [MFC], InsertAt
- CTypedPtrArray [MFC], SetAt
- CTypedPtrArray [MFC], SetAtGrow
ms.assetid: e3ecdf1a-a889-4156-92dd-ddbd36ccd919
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c9082e28aad1edc584a1796d5bb5e97b5601753f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122918"
---
# <a name="ctypedptrarray-class"></a>Ctypedptrarray — klasa
Udostępnia bezpieczne "otoki" dla obiektów klasy `CPtrArray` lub `CObArray`.  
  
## <a name="syntax"></a>Składnia  
  
```  
template<class BASE_CLASS, class TYPE>  
class CTypedPtrArray : public BASE_CLASS  
```  
  
#### <a name="parameters"></a>Parametry  
 *BASE_CLASS*  
 Klasa podstawowa klasy array typizowaną wskaźnika; musi być klasą tablicy ( `CObArray` lub `CPtrArray`).  
  
 *TYP*  
 Typ elementów przechowywane w tablicy klasy podstawowej.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CTypedPtrArray::Add](#add)|Dodaje nowy element do końca tablicy. Rozwoju tablicy, w razie potrzeby|  
|[CTypedPtrArray::Append](#append)|Dodaje zawartość tablicy w celu innego. Rozwoju tablicy, w razie potrzeby|  
|[CTypedPtrArray::Copy](#copy)|Kopiuje innej tablicy do tablicy; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
|[CTypedPtrArray::ElementAt](#elementat)|Zwraca tymczasowego odwołanie do wskaźnika elementu w tablicy.|  
|[CTypedPtrArray::GetAt](#getat)|Zwraca wartość pod danym indeksem.|  
|[CTypedPtrArray::InsertAt](#insertat)|Wstawia elementu (lub wszystkie elementy w innej tablicy) od określonego indeksu.|  
|[CTypedPtrArray::SetAt](#setat)|Ustawia wartość dla danego indeksu; Tablica nie może wzrosnąć.|  
|[CTypedPtrArray::SetAtGrow](#setatgrow)|Ustawia wartość dla danego indeksu; Jeśli to konieczne, zwiększa rozmiar tablicy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[[CTypedPtrArray::operator]](#operator_at)|Ustawia lub pobiera element pod określonym indeksem.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz `CTypedPtrArray` zamiast `CPtrArray` lub `CObArray`, funkcji Kontrola typów języka C++ pozwala wyeliminować błędy spowodowane przez wskaźnik niezgodne typy.  
  
 Ponadto `CTypedPtrArray` otoki wykonuje większość rzutowanie, które będą wymagane, jeśli używasz `CObArray` lub `CPtrArray`.  
  
 Ponieważ wszystkie `CTypedPtrArray` funkcje są wbudowane, użyj tego szablonu nie znacząco wpływa na rozmiar lub prędkość kodu.  
  
 Aby uzyskać więcej informacji na temat używania `CTypedPtrArray`, zobacz artykuły [kolekcje](../../mfc/collections.md) i [na podstawie szablonu klasy](../../mfc/template-based-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `BASE_CLASS`  
  
 `CTypedPtrArray`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afxtempl.h  
  
##  <a name="add"></a>  CTypedPtrArray::Add  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: Dodaj**.  
  
```  
INT_PTR Add(TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementu do dodania do tablicy.  
  
 *newElement*  
 Element, który ma zostać dodany do tej tablicy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks elementu dodany.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Add](../../mfc/reference/cobarray-class.md#add).  
  
##  <a name="append"></a>  CTypedPtrArray::Append  
 Wywołania funkcji członkowskiej `BASE_CLASS`:: Append **.  
  
```  
INT_PTR Append(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Parametry  
 *BASE_CLASS*  
 Klasa podstawowa klasy array typizowaną wskaźnika; musi być klasą tablicy ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TYP*  
 Typ elementów przechowywane w tablicy klasy podstawowej.  
  
 *src*  
 Źródło elementów do dołączenia do macierzy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Indeks pierwszego elementu dołączany.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Append](../../mfc/reference/cobarray-class.md#append).  
  
##  <a name="copy"></a>  CTypedPtrArray::Copy  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: kopiowania**.  
  
```  
void Copy(const CTypedPtrArray<BASE_CLASS, TYPE>& src);
```  
  
### <a name="parameters"></a>Parametry  
 *BASE_CLASS*  
 Klasa podstawowa klasy array typizowaną wskaźnika; musi być klasą tablicy ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *TYP*  
 Typ elementów przechowywane w tablicy klasy podstawowej.  
  
 *src*  
 Źródło elementów do skopiowania do tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::Copy](../../mfc/reference/cobarray-class.md#copy).  
  
##  <a name="elementat"></a>  CTypedPtrArray::ElementAt  
 Wywołania tej funkcji wbudowanej `BASE_CLASS` **:: ElementAt**.  
  
```  
TYPE& ElementAt(INT_PTR nIndex);
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Parametr szablonu określający typ elementów przechowywanych w tej macierzy.  
  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Tymczasowe odwołanie do elementu w lokalizacji określonej przez *nIndex*. Ten element jest typu określonego przez parametr szablonu *typu*.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat).  
  
##  <a name="getat"></a>  CTypedPtrArray::GetAt  
 Wywołania tej funkcji wbudowanej `BASE_CLASS` **:: GetAt**.  
  
```  
TYPE GetAt(INT_PTR nIndex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określenie typu elementy przechowywane w tablicy parametrów szablonu.  
  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopia elementu w lokalizacji określonej przez *nIndex*. Ten element jest typu określonego przez parametr szablonu *typu*.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)  
  
##  <a name="insertat"></a>  CTypedPtrArray::InsertAt  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: InsertAt**.  
  
```  
void InsertAt(
    INT_PTR nIndex,  
    TYPE newElement,  
    INT_PTR nCount = 1);

 
void InsertAt(
    INT_PTR nStartIndex,  
    CTypedPtrArray<BASE_CLASS, TYPE>* pNewArray);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TYP*  
 Typ elementów przechowywane w tablicy klasy podstawowej.  
  
 *newElement*  
 Wskaźnik do obiektu mają być umieszczone w tej macierzy. A *newElement* wartości **NULL** jest dozwolone.  
  
 *nCount*  
 Ile razy ten element powinien być wstawiane (wartość domyślna to 1).  
  
 *nStartIndex*  
 Liczba całkowita indeksu, który może być większa niż wartość zwrócona przez `CObArray::GetUpperBound`.  
  
 *BASE_CLASS*  
 Klasa podstawowa klasy array typizowaną wskaźnika; musi być klasą tablicy ( [CObArray](../../mfc/reference/cobarray-class.md) lub [CPtrArray](../../mfc/reference/cptrarray-class.md)).  
  
 *pNewArray*  
 Innej tablicy, który zawiera elementy, które mają zostać dodane do tej tablicy.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat).  
  
##  <a name="operator_at"></a>  [CTypedPtrArray::operator]  
 Wywołania tych operatorów wbudowanego `BASE_CLASS` **:: — operator []**.  
  
```  
TYPE& operator[ ](int_ptr nindex);  
TYPE operator[ ](int_ptr nindex) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *TYP*  
 Określenie typu elementy przechowywane w tablicy parametrów szablonu.  
  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez `BASE_CLASS` **:: GetUpperBound**.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy operator o nazwie dla tablic, które nie są **const**, mogą być używane w prawo (r) lub z lewej strony (wartości l) instrukcji przypisania. Druga Strona, wywołane **const** tablic, mogą służyć tylko po prawej stronie.  
  
 Wersja do debugowania biblioteki potwierdza, jeśli indeks dolny (albo po lewej lub prawej stronie instrukcji przypisania) jest poza zakresem.  
  
##  <a name="setat"></a>  CTypedPtrArray::SetAt  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: SetAt**.  
  
```  
void SetAt(
    INT_PTR nIndex,  
    TYPE ptr);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0 i mniejsza niż wartość zwrócona przez [CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound).  
  
 *TYP*  
 Typ elementów przechowywane w tablicy klasy podstawowej.  
  
 *ptr*  
 Wskaźnik do elementu, który ma zostać wstawiony w tablicy w nIndex. Wartość NULL jest dozwolona.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat).  
  
##  <a name="setatgrow"></a>  CTypedPtrArray::SetAtGrow  
 Wywołania funkcji członkowskiej `BASE_CLASS` **:: SetAtGrow**.  
  
```  
void SetAtGrow(
    INT_PTR nIndex,  
    TYPE newElement);
```  
  
### <a name="parameters"></a>Parametry  
 *nIndex*  
 Liczba całkowita indeksu, który jest większa lub równa 0.  
  
 *TYP*  
 Typ elementów przechowywane w tablicy klasy podstawowej.  
  
 *newElement*  
 Wskaźnik obiektu ma zostać dodany do tej tablicy. A **NULL** wartość jest dozwolona.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać bardziej szczegółowe uwagi, zobacz [CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow).  
  
## <a name="see-also"></a>Zobacz też  
 [Przykładowe MFC ZBIERANIE](../../visual-cpp-samples.md)   
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [Klasa CPtrArray](../../mfc/reference/cptrarray-class.md)   
 [Klasa CObArray](../../mfc/reference/cobarray-class.md)
