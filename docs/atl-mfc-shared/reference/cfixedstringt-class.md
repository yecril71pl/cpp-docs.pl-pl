---
title: CFixedStringT, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 213bfd9dc5c07ad1b3ef811b9333cb12bf9c2b7a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755604"
---
# <a name="cfixedstringt-class"></a>CFixedStringT, klasa

Ta klasa reprezentuje obiekt ciągu z buforem stałych znaków.

## <a name="syntax"></a>Składnia

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parametry

*StringType*  
Używane jako klasa bazowa dla obiektu stały ciąg i może być dowolnym `CStringT`— na podstawie typu. Niektóre przykłady `CString`, `CStringA`, i `CStringW`.

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

Ta klasa jest przykładem klasy niestandardowy ciąg na podstawie `CStringT`. Mimo że jest to bardzo podobne w implementacji różnią się dwóch klas. Główne różnice między `CFixedStringT` i `CStringT` są:

- Bufor początkowy znak jest przydzielany w ramach obiektu, a ma rozmiar *t_nChars*. Dzięki temu `CFixedString` obiektu zajmować fragment ciągłej pamięci dla celów wydajności. Jednakże jeśli zawartość `CFixedStringT` przekroczy obiektu *t_nChars*, bufor jest przydzielany dynamicznie.

- Bufor znaków dla `CFixedStringT` obiektu jest zawsze tę samą długość ( *t_nChars*). Nie ma ograniczeń dotyczących rozmiaru buforu dla `CStringT` obiektów.

- Menedżer pamięci dla `CFixedStringT` został dostosowany w taki sposób, że udostępnianie [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) obiektu między co najmniej dwóch `CFixedStringT` objectsis niedozwolone. `CStringT` obiekty nie mają tego ograniczenia.

Aby uzyskać więcej informacji na temat dostosowywania `CFixedStringT` i ogólnie rzecz biorąc, zobacz Zarządzanie pamięci dla obiektów w postaci ciągów [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** cstringt.h

##  <a name="cfixedstringt"></a>  CFixedStringT::CFixedStringT

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

*psz*  
Ciąg zakończony wartością null do skopiowania do tego `CFixedStringT` obiektu.

*str*  
Istniejące `CFixedStringT` obiektu do skopiowania do tego `CFixedStringT` obiektu.

*pStringMgr*  
Wskaźnik do Menedżera pamięci `CFixedStringT` obiektu. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięci dla `CFixedStringT`, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Uwagi

Konstruktory skopiować dane wejściowe do nowego magazynu przydzielone, dlatego należy pamiętać, że pamięć wyjątków może spowodować. Należy pamiętać, że niektóre z tych konstruktorów pełnią funkcje konwersji.

##  <a name="operator__eq"></a>  CFixedStringT::operator =

Ponownie inicjuje istniejące `CFixedStringT` obiektu za pomocą nowych danych.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& str);
CFixedStringT<StringType, t_nChars>& operator=(const char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* psz);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* psz);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& str);
```

### <a name="parameters"></a>Parametry

*str*  
Ciąg zakończony wartością null do skopiowania do tego `CFixedStringT` obiektu.

*psz*  
Istniejące `CFixedStringT` do skopiowania do tego `CFixedStringT` obiektu.

### <a name="remarks"></a>Uwagi

Należy zwrócić uwagę pamięci wyjątki mogą wystąpić przy każdym użyciu operatora przypisania, ponieważ nowy magazyn często jest przeznaczona do przechowywania, wynikowy `CFixedStringT` obiektu.

## <a name="see-also"></a>Zobacz też

[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)   
[Diagram hierarchii](../../mfc/hierarchy-chart.md)   
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)

