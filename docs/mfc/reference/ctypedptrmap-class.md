---
title: Ctypedptrmap — klasa
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
ms.openlocfilehash: 4c6d20279792788c1013df8540080b2715ade1f2
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657386"
---
# <a name="ctypedptrmap-class"></a>Ctypedptrmap — klasa

Oferuje bezpieczne "opakowanie" dla klas wskaźnika map `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, i `CMapStringToPtr`.

## <a name="syntax"></a>Składnia

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Parametry

*ELEMENT $BASE_CLASS*<br/>
Klasą bazową klasy mapy wpisane wskaźnika; musi być klasą mapy wskaźnika ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, lub `CMapStringToPtr`).

*KEY*<br/>
Klasa Obiekt używany jako klucz do mapy.

*WARTOŚĆ*<br/>
Klasa obiektu przechowywany w mapie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Pobiera następny element do wykonania iteracji.|
|[CTypedPtrMap::Lookup](#lookup)|Zwraca `KEY` na podstawie `VALUE`.|
|[CTypedPtrMap::RemoveKey](#removekey)|Usuwa element określony przez klucz.|
|[CTypedPtrMap::SetAt](#setat)|Wstawia element do mapy; zastępuje istniejący element, jeśli dopasowany klucz zostanie znaleziony.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CTypedPtrMap::operator \[ \]](#operator_at)|Wstawia element do mapy.|

## <a name="remarks"></a>Uwagi

Kiedy używasz `CTypedPtrMap`, funkcji Kontrola typów w języku C++, pomaga wyeliminować sytuację błędów spowodowanych przez wskaźnik niezgodne typy.

Ponieważ wszystkie `CTypedPtrMap` funkcje są wbudowane, użyj tego szablonu nie znacząco wpływa na rozmiar lub prędkość kodu.

Aby uzyskać więcej informacji na temat korzystania z `CTypedPtrMap`, zobacz artykuły [kolekcje](../../mfc/collections.md) i [oparte na szablonach klas](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxtempl.h

##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc

Pobiera element mapy w `rNextPosition`, następnie aktualizuje `rNextPosition` do odwoływania się do następnego elementu w mapie.

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*elemencie rPosition*<br/>
Określa odwołanie do wartości pozycji zwrócony przez poprzednie `GetNextAssoc` lub `BASE_CLASS` **:: GetStartPosition** wywołania.

*KEY*<br/>
Parametr szablonu określający typ mapy kluczy.

*rKey*<br/>
Określa klucz zwróconego elementu pobrane.

*WARTOŚĆ*<br/>
Parametr szablonu określający typ wartości mapy.

*r-wartości*<br/>
Określa wartość elementu pobrane.

### <a name="remarks"></a>Uwagi

Ta funkcja jest najbardziej przydatne do iteracji na elementach na mapie. Należy pamiętać, że sekwencja pozycji niekoniecznie jest taka sama jak wartość klucza sekwencji.

Jeśli element pobrane jest ostatni w mapie, nowa wartość `rNextPosition` ma wartość NULL.

Ta funkcja śródwierszowa wywołuje `BASE_CLASS` **:: GetNextAssoc**.

##  <a name="lookup"></a>  CTypedPtrMap::Lookup

`Lookup` używa algorytmu wyznaczania wartości skrótu, aby szybko znaleźć element mapy za pomocą klucza, który dokładnie pasuje.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parametry

*ELEMENT $BASE_CLASS*<br/>
Parametr szablonu określający klasą bazową klasy tej mapie.

*Klucz*<br/>
Klucz elementu, który ma być wyszukiwana.

*WARTOŚĆ*<br/>
Parametr szablonu określający typ wartości przechowywanych na tej mapie.

*r-wartości*<br/>
Określa wartość elementu pobrane.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli element został znaleziony; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ta funkcja śródwierszowa wywołuje `BASE_CLASS` **:: wyszukiwania**.

##  <a name="operator_at"></a>  [] CTypedPtrMap::operator

Ten operator może służyć tylko z lewej instrukcji przypisania (l wartości).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Parametry

*WARTOŚĆ*<br/>
Parametr szablonu określający typ wartości przechowywanych na tej mapie.

*ELEMENT $BASE_CLASS*<br/>
Parametr szablonu określający klasą bazową klasy tej mapie.

*Klucz*<br/>
Klucz elementu mają być wyszukiwane lub utworzony w mapie.

### <a name="remarks"></a>Uwagi

Jeśli nie ma żadnego elementu na mapie, z określonym kluczem, nowy element zostanie utworzony. Istnieje nie "po prawej stronie" (r) odpowiednikiem tego operatora, ponieważ istnieje możliwość, że nie można znaleźć klucza w mapie. Użyj `Lookup` funkcja elementu członkowskiego do elementu pobierania.

##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Parametry

*KEY*<br/>
Parametr szablonu określający typ mapy kluczy.

*Klucz*<br/>
Klucz elementu do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli wpis zostało znalezione i pomyślnie usunął; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

##  <a name="setat"></a>  CTypedPtrMap::SetAt

Ta funkcja elementu członkowskiego wywołuje `BASE_CLASS` **:: SetAt**.

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Parametry

*KEY*<br/>
Parametr szablonu określający typ mapy kluczy.

*Klucz*<br/>
Określa wartość klucza newValue.

*newValue*<br/>
Określa wskaźnik do obiektu, który jest wartością nowego elementu.

### <a name="remarks"></a>Uwagi

Aby uzyskać bardziej szczegółowe uwagi, zobacz [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Zobacz też

[Próbki MFC ZBIERANIE](../../visual-cpp-samples.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasa CMapPtrToPtr](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[Klasa CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)<br/>
[Klasa CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[Klasa CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)
