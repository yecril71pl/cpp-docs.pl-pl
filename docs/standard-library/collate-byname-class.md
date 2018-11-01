---
title: collate_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate_byname
helpviewer_keywords:
- collate_byname class
ms.assetid: 3dc380df-867c-4763-b60e-ba62a8e63ca7
ms.openlocfilehash: 46eb139bafcf7368688f32cce37e38362c158c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569604"
---
# <a name="collatebyname-class"></a>collate_byname — Klasa

Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł sortowania danych ustawień regionalnych, umożliwiając pobieranie informacji specyficznych dla obszaru kulturowego dotyczących konwencji sortowania ciągów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class collate_byname : public collate<CharType> {
public:
    explicit collate_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit collate_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~collate_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname*<br/>
O nazwie ustawienia regionalne.

*_Refs*<br/>
Licznik odwołań początkowej.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje obiekt, który może służyć jako [reguł ustawień regionalnych](../standard-library/locale-class.md#facet_class) typu [collate](../standard-library/collate-class.md#collate)\<CharType >. Jego zachowanie jest określana przez [o nazwie](../standard-library/locale-class.md#name) ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje jego podstawowego obiektu z [collate](../standard-library/collate-class.md#collate)\<CharType > ( `_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
