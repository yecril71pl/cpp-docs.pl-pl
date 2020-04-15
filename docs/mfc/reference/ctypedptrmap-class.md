---
title: Klasa CTypedPtrMap
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: 41416c8223ac94364e8f83028ea93189e9f3f60c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373258"
---
# <a name="ctypedptrmap-class"></a>Klasa CTypedPtrMap

Zapewnia bezpieczne dla typu "otokę" dla obiektów `CMapPtrToPtr`klas `CMapPtrToWord` `CMapWordToPtr`mapy `CMapStringToPtr`wskaźnika , i .

## <a name="syntax"></a>Składnia

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Klasa podstawowa klasy mapy wpisanego wskaźnika; musi być klasą `CMapPtrToPtr`mapy `CMapPtrToWord` `CMapWordToPtr`wskaźnika `CMapStringToPtr`( , , , lub ).

*Klucz*<br/>
Klasa obiektu używanego jako klucz do mapy.

*Wartość*<br/>
Klasa obiektu przechowywanego na mapie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Pobiera następny element do iteracji.|
|[CTypedPtrMap::Odnośnik](#lookup)|Zwraca `KEY` na podstawie `VALUE`.|
|[CTypedPtrMap::RemoveKey](#removekey)|Usuwa element określony przez klucz.|
|[CTypedPtrMap::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli zostanie znaleziony pasujący klucz.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrMap::operator \[\]](#operator_at)|Wstawia element do mapy.|

## <a name="remarks"></a>Uwagi

Podczas korzystania `CTypedPtrMap`z funkcji sprawdzania typu języka C++ pomaga wyeliminować błędy spowodowane niedopasowanymi typami wskaźników.

Ponieważ `CTypedPtrMap` wszystkie funkcje są wbudowane, użycie tego szablonu nie ma znaczącego wpływu na rozmiar lub szybkość kodu.

Aby uzyskać więcej `CTypedPtrMap`informacji na temat używania , zobacz artykuły [Kolekcje](../../mfc/collections.md) i [klasy oparte na szablonach](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc

Pobiera element mapy `rNextPosition`w , `rNextPosition` a następnie aktualizacje, aby odwołać się do następnego elementu na mapie.

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*rPozycja*<br/>
Określa odwołanie do wartości POSITION zwróconej `GetNextAssoc` `BASE_CLASS`przez poprzednie wywołanie **getstartposition.**

*Klucz*<br/>
Parametr szablonu określający typ kluczy mapy.

*rKey (Klawisz)*<br/>
Określa zwracany klucz pobranego elementu.

*Wartość*<br/>
Parametr szablonu określający typ wartości mapy.

*rWartość*<br/>
Określa zwracaną wartość pobranego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja jest najbardziej przydatna do iteracji przez wszystkie elementy na mapie. Należy zauważyć, że sekwencja pozycji nie musi być taka sama jak sekwencja wartości klucza.

Jeśli pobrany element jest ostatnim na mapie, nowa `rNextPosition` wartość jest ustawiona na WARTOŚĆ NULL.

Ta wbudowana `BASE_CLASS`funkcja wywołuje **::GetNextAssoc**.

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a>CTypedPtrMap::Odnośnik

`Lookup`używa algorytmu mieszania, aby szybko znaleźć element mapy z kluczem, który dokładnie odpowiada.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*BASE_CLASS*<br/>
Parametr szablonu określający klasę podstawową tej klasy mapy.

*key*<br/>
Klucz elementu, który ma być spojrzał w górę.

*Wartość*<br/>
Parametr szablonu określający typ wartości przechowywanych na tej mapie.

*rWartość*<br/>
Określa zwracaną wartość pobranego elementu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli element został znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta wbudowana `BASE_CLASS`funkcja wywołuje **::Lookup**.

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a>CTypedPtrMap::operator [ ]

Ten operator może być używany tylko po lewej stronie instrukcji przypisania (wartość l).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Parametry

*Wartość*<br/>
Parametr szablonu określający typ wartości przechowywanych na tej mapie.

*BASE_CLASS*<br/>
Parametr szablonu określający klasę podstawową tej klasy mapy.

*key*<br/>
Klucz elementu, który ma być spojrzał w górę lub utworzony na mapie.

### <a name="remarks"></a>Uwagi

Jeśli nie ma żadnego elementu mapy z określonym kluczem, tworzony jest nowy element. Nie ma "prawej strony" (r-value) równoważne tego operatora, ponieważ istnieje możliwość, że klucz nie można znaleźć na mapie. Użyj `Lookup` funkcji elementu członkowskiego do pobierania elementu.

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a>CTypedPtrMap::RemoveKey

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Parametr szablonu określający typ kluczy mapy.

*key*<br/>
Klucz do usunięcia elementu.

### <a name="return-value"></a>Wartość zwracana

Nonzero, jeśli wpis został znaleziony i pomyślnie usunięte; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

## <a name="ctypedptrmapsetat"></a><a name="setat"></a>CTypedPtrMap::SetAt

Ta funkcja `BASE_CLASS`elementu członkowskiego wywołuje **::SetAt**.

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Parametry

*Klucz*<br/>
Parametr szablonu określający typ kluczy mapy.

*key*<br/>
Określa wartość klucza newValue.

*Newvalue*<br/>
Określa wskaźnik obiektu, który jest wartością nowego elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Zobacz też

[MFC Próbki COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[Klasa CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)<br/>
[Klasa CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[Klasa CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)
