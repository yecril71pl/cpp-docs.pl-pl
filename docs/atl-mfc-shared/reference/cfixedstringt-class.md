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
ms.openlocfilehash: fe096185f6f0b71ad45757cd0b75ab13c41e5f5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317825"
---
# <a name="cfixedstringt-class"></a>CFixedStringT, klasa

Ta klasa reprezentuje obiekt ciąg ze stałym buforem znaków.

## <a name="syntax"></a>Składnia

```
template<class StringType, int t_nChars>
class CFixedStringT : private CFixedStringMgr, public StringType
```

#### <a name="parameters"></a>Parametry

*Typ ciągu*<br/>
Używany jako klasa podstawowa dla obiektu stałego ciągu i może być dowolny `CStringT`typ oparty na. Niektóre przykłady `CString` `CStringA`obejmują `CStringW`, i .

*t_nChars*<br/>
Liczba znaków przechowywanych w buforze.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFixedStringT::CFixedStringT](#cfixedstringt)|Konstruktor dla obiektu ciągu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CFixedStringT::operator =](#operator_eq)|Przypisuje nową wartość do `CFixedStringT` obiektu.|

## <a name="remarks"></a>Uwagi

Ta klasa jest przykładem niestandardowej `CStringT`klasy ciągu opartej na programie . Chociaż podobne, dwie klasy różnią się w implementacji. Główne różnice `CFixedStringT` między `CStringT` i są:

- Początkowy bufor znaków jest przydzielany jako część obiektu i ma rozmiar *t_nChars*. Dzięki temu `CFixedString` obiekt zajmuje ciągły fragment pamięci dla celów wydajności. Jeśli jednak zawartość `CFixedStringT` obiektu wzrośnie poza *t_nChars,* bufor jest przydzielany dynamicznie.

- Bufor znaków dla `CFixedStringT` obiektu ma zawsze taką samą długość ( *t_nChars*). Nie ma ograniczeń co `CStringT` do rozmiaru buforu dla obiektów.

- Menedżer pamięci `CFixedStringT` dla jest dostosowany w taki sposób, że udostępnianie `CFixedStringT` [CStringData](../../atl-mfc-shared/reference/cstringdata-class.md) obiektu między dwoma lub więcej obiektów jest niedozwolone. `CStringT`obiekty nie mają tego ograniczenia.

Aby uzyskać więcej informacji `CFixedStringT` na temat dostosowywania i zarządzania pamięcią dla obiektów ciągów w ogóle, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlStringMgr`

`StringType`

`CFixedStringMgr`

`CFixedStringT`

## <a name="requirements"></a>Wymagania

**Nagłówek:** cstringt.h

## <a name="cfixedstringtcfixedstringt"></a><a name="cfixedstringt"></a>CFixedStringT::CFixedStringT

Konstruuje `CFixedStringT` obiekt.

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

*pszsrc*<br/>
Ciąg zakończony z wartością null ma `CFixedStringT` zostać skopiowany do tego obiektu.

*strSrc ( strSrc )*<br/>
Istniejący `CFixedStringT` obiekt do skopiowania `CFixedStringT` do tego obiektu.

*pStringMgr*<br/>
Wskaźnik do menedżera pamięci `CFixedStringT` obiektu. Aby uzyskać `IAtlStringMgr` więcej informacji `CFixedStringT`na temat zarządzania pamięcią i zarządzania pamięcią dla , zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

### <a name="remarks"></a>Uwagi

Ponieważ konstruktory skopiować dane wejściowe do nowego przydzielonego magazynu, należy pamiętać, że wyjątki pamięci może spowodować. Niektóre z tych konstruktorów działają jako funkcje konwersji.

## <a name="cfixedstringtoperator-"></a><a name="operator_eq"></a>CFixedStringT::operator =

Reinityzuje istniejący `CFixedStringT` obiekt z nowymi danymi.

```
CFixedStringT<StringType, t_nChars>& operator=(
    const CFixedStringT<StringType, t_nChars>& strSrc);
CFixedStringT<StringType, t_nChars>& operator=(const char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const wchar_t* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const unsigned char* pszSrc);
CFixedStringT<StringType, t_nChars>& operator=(const StringType& strSrc);
```

### <a name="parameters"></a>Parametry

*pszsrc*<br/>
Ciąg zakończony z wartością null ma `CFixedStringT` zostać skopiowany do tego obiektu.

*strSrc ( strSrc )*<br/>
Istniejący `CFixedStringT` do skopiowania `CFixedStringT` do tego obiektu.

### <a name="remarks"></a>Uwagi

Należy pamiętać, że wyjątki pamięci mogą wystąpić za każdym razem, gdy używasz `CFixedStringT` operatora przypisania, ponieważ nowy magazyn jest często przydzielany do przechowywania wynikowego obiektu.

## <a name="see-also"></a>Zobacz też

[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
