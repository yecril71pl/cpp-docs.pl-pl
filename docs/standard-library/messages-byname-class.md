---
title: messages_byname — Klasa
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: 7b341f3e1dbf76021911c70560b83932b5302191
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605340"
---
# <a name="messagesbyname-class"></a>messages_byname — Klasa

Klasa pochodna szablonu opisująca obiekt, który może służyć jako zestaw reguł komunikatów danych ustawień regionalnych, umożliwiając pobieranie zlokalizowanych komunikatów.

## <a name="syntax"></a>Składnia

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>Parametry

*_Locname*<br/>
O nazwie ustawienia regionalne.

*_Refs*<br/>
Licznik odwołań początkowej.

## <a name="remarks"></a>Uwagi

Jego zachowanie jest określana przez nazwany ustawień regionalnych *_Locname*. Każdy Konstruktor inicjuje jego podstawowego obiektu z [wiadomości](../standard-library/messages-class.md#messages)\<CharType > ( `_Refs`).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ustawień regionalnych >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
