---
title: pointer_to_unary_function — Klasa
ms.date: 02/21/2019
f1_keywords:
- functional/std::pointer_to_unary
helpviewer_keywords:
- pointer_to_unary_function function
- pointer_to_unary_function class
ms.assetid: 05600207-b916-4759-beca-6b6facd2d6f6
ms.openlocfilehash: 710453711e60f4607a20eb3e71b65127c8dd5316
ms.sourcegitcommit: 4299caac2dc9e806c74ac833d856a3838b0f52a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "57006659"
---
# <a name="pointertounaryfunction-class"></a>pointer_to_unary_function — Klasa

Konwertuje funkcję jednoargumentową potężnej jednoargumentowe wskaźnika funkcji. Przestarzałe w C ++ 11, usunięte w języku C ++ 17.

## <a name="syntax"></a>Składnia

```cpp
template <class Arg, class Result>
class pointer_to_unary_function
    : public unary_function<Arg, Result>
{
public:
    explicit pointer_to_unary_function(Result(*pfunc)(Arg));
    Result operator()(Arg left) const;
};
```

### <a name="parameters"></a>Parametry

*pfunc*<br/>
Binarny funkcja, która ma zostać przekonwertowany.

*left*<br/>
Obiekt,  *\*pfunc* jest wywoływana w.

## <a name="return-value"></a>Wartość zwracana

Klasa szablonu przechowuje kopię `pfunc`. Definiuje jej funkcji członkowskiej `operator()` powrotu (\* **pfunc**) (_ *po lewej stronie*).

## <a name="remarks"></a>Uwagi

Jednoargumentowy wskaźnika funkcji jest obiektem funkcji i może być przekazywany do dowolnego algorytmu biblioteki standardowej języka C++, który oczekuje funkcję jednoargumentową jako parametru, ale nie jest dostosowana. Do korzystania z adaptera, takich jak powiązania wartości do niego lub użyciu negator, należy podać przy użyciu typów zagnieżdżonych `argument_type` i `result_type` , umożliwiają dostosowanie takie. Konwersja przez `pointer_to_unary_function` umożliwia adapterów funkcji do pracy z wskaźników funkcji binarnego.

## <a name="example"></a>Przykład

Konstruktor obiektu `pointer_to_unary_function` jest rzadko używana bezpośrednio. Zobacz opis funkcji pomocnika [ptr_fun —](../standard-library/functional-functions.md#ptr_fun) przykładowy sposób deklarowania i użyj `pointer_to_unary_function` predykatu adaptera.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<funkcjonalności >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
