---
title: enable_shared_from_this — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- memory/std::enable_shared_from_this
dev_langs:
- C++
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46e5b0b0c55c5a5dd0a48d2437fc83fa43226f5a
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38956147"
---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this — Klasa

Ułatwia generowanie `shared_ptr`.

## <a name="syntax"></a>Składnia

```cpp
class enable_shared_from_this {
public:
    shared_ptr<Ty>
        shared_from_this();
    shared_ptr<const Ty> shared_from_this() const;
protected:
    enable_shared_from_this();
    enable_shared_from_this(const enable_shared_from_this&);
    enable_shared_from_this& operator=(const enable_shared_from_this&);
    ~enable_shared_from_this();
};
```

### <a name="parameters"></a>Parametry

*Ty* typ kontrolowany przez dzielony wskaźnik.

## <a name="remarks"></a>Uwagi

Obiekty pochodzące z `enable_shared_from_this` służy `shared_from_this` metod w funkcji elementów członkowskich, aby utworzyć [shared_ptr](../standard-library/shared-ptr-class.md) właścicieli wystąpienia, które dzielą prawo własności przy użyciu istniejących `shared_ptr` właścicieli. W przeciwnym razie, jeśli tworzysz nową `shared_ptr` przy użyciu **to**, różni się on od istniejących `shared_ptr` właścicieli, co może prowadzić do nieprawidłowe odwołania lub powodują, że obiekt można usunąć więcej niż jeden raz.

Konstruktory, destruktor i operator przypisania są chronione, aby uniknąć przypadkowego nadużycie. Typ argumentu szablonu *Ty* musi być typem klasy pochodnej.

Na przykład użycie zobacz [enable_shared_from_this::shared_from_this](#shared_from_this).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="shared_from_this"></a>  enable_shared_from_this::shared_from_this

Generuje `shared_ptr` , udostępnia własności wystąpienie z istniejącym `shared_ptr` właścicieli.

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>Uwagi

Po utworzeniu klasy pochodnej obiektów z `enable_shared_from_this` podstawowej klasy, `shared_from_this` składowej szablonu funkcje zwracają [shared_ptr — klasa](../standard-library/shared-ptr-class.md) obiektu, który udostępnia własności tego wystąpienia przy użyciu istniejących `shared_ptr` właścicieli. W przeciwnym razie, jeśli tworzysz nową `shared_ptr` z **to**, różni się on od istniejących `shared_ptr` właścicieli, co może prowadzić do nieprawidłowe odwołania lub powodują, że obiekt można usunąć więcej niż jeden raz. Zachowanie jest niezdefiniowane, jeśli wywołasz `shared_from_this` wystąpieniu, który nie jest już własnością `shared_ptr` obiektu.

### <a name="example"></a>Przykład

```cpp
// std_memory_shared_from_this.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

struct base : public std::enable_shared_from_this<base>
{
    int val;
    shared_ptr<base> share_more()
    {
        return shared_from_this();
    }
};

int main()
{
    auto sp1 = make_shared<base>();
    auto sp2 = sp1->share_more();

    sp1->val = 3;
    cout << "sp2->val == " << sp2->val << endl;
    return 0;
}
```

```Output
sp2->val == 3
```

## <a name="see-also"></a>Zobacz także

[enable_shared_from_this::shared_from_this](#shared_from_this)<br/>
[shared_ptr, klasa](../standard-library/shared-ptr-class.md)<br/>