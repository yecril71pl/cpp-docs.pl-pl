---
title: CFixedStringT, klasa
ms.date: 03/27/2019
f1_keywords:
- CFixedStringT
- CSTRINGT/ATL::CFixedStringT
- CSTRINGT/ATL::CFixedStringT::CFixedStringT
helpviewer_keywords:
- CFixedStringT class
- shared classes, CFixedStringT
ms.assetid: 6d4171ba-3104-493a-a6cc-d515f4ba9a4b
ms.openlocfilehash: 6c7649b7131e3b1620112acf89867d0731d7265d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235168"
---
# <a name="cfixedstringt-class"></a>CFixedStringT, klasa

Ta klasa reprezentuje obiekt ciągu z buforem stałych znaków.

## <a name="syntax"></a>Składnia

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parametry

*StringType*<br/>
Używane jako klasa bazowa dla obiektu stały ciąg i może być dowolnym `CStringT`— na podstawie typu. Niektóre przykłady `CString`, `CStringA`, i `CStringW`.

*t_nChars*<br/>
Liczba znaków przechowywanych w buforze.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|Konstruktor z obiektem ciągu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFixedStringT::operator =](#operator_eq)|Przypisuje nową wartość do `CFixedStringT` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa jest przykładem klasy niestandardowy ciąg na podstawie `CStringT`. Mimo że jest to podobne, dwie klasy różnią się w celu wykonania. Główne różnice między `CFixedStringT` i `CStringT` są:

- Bufor początkowy znak jest przydzielany w ramach obiektu, a ma rozmiar *t_nChars*. Dzięki temu `CFixedString` obiektu zajmować fragment ciągłej pamięci dla celów wydajności. Jednakże jeśli zawartość `CFixedStringT` przekroczy obiektu *t_nChars*, bufor jest przydzielany dynamicznie.

- Bufor znaków dla `CFixedStringT` obiektu jest zawsze tę samą długość ( *t_nChars*). Nie ma ograniczeń dotyczących rozmiaru buforu dla `CStringT` obiektów.

- Menedżer pamięci dla `CFixedStringT` został dostosowany w taki sposób, że udostępnianie [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) obiektu między co najmniej dwóch `CFixedStringT` obiektów jest niedozwolona. `CStringT` obiekty nie mają tego ograniczenia.

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
CFixedStringT(const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT(const StringType& strSrc);
CFixedStringT(const StringType::XCHAR* pszSrc);
explicit CFixedStringT(const StringType::YCHAR* pszSrc);
explicit CFixedStringT(const unsigned char* pszSrc);
```

### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ciąg zakończony wartością null do skopiowania do tego `CFixedStringT` obiektu.

*strSrc*<br/>
Istniejące `CFixedStringT` obiektu do skopiowania do tego `CFixedStringT` obiektu.

*pStringMgr*<br/>
Wskaźnik do Menedżera pamięci `CFixedStringT` obiektu. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięci dla `CFixedStringT`, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Uwagi

Konstruktory skopiować dane wejściowe do nowego magazynu przydzielone, dlatego należy pamiętać, że pamięć wyjątków może spowodować. Niektóre z tych konstruktorów pełnią funkcje konwersji.

##  <a name="operator_eq"></a>  CFixedStringT::operator =

Ponownie inicjuje istniejące `CFixedStringT` obiektu za pomocą nowych danych.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Ciąg zakończony wartością null do skopiowania do tego `CFixedStringT` obiektu.

*strSrc*<br/>
Istniejące `CFixedStringT` do skopiowania do tego `CFixedStringT` obiektu.

### <a name="remarks"></a>Uwagi

Należy zwrócić uwagę pamięci wyjątki mogą wystąpić przy każdym użyciu operatora przypisania, ponieważ nowy magazyn często jest przeznaczona do przechowywania, wynikowy `CFixedStringT` obiektu.

## <a name="see-also"></a>Zobacz także

[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
