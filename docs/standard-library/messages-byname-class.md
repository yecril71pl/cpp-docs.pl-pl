---
title: messages_byname — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmes/std::messages_byname
dev_langs:
- C++
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e03cb627e7e9db40d56a69112977d87141626696
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100447"
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
