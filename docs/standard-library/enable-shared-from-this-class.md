---
title: enable_shared_from_this — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- memory/std::enable_shared_from_this
dev_langs:
- C++
helpviewer_keywords:
- enable_shared_from_this class
- enable_shared_from_this
ms.assetid: 9237603d-22e2-421f-b070-838ac006baf5
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6dbe32a248475cad26dae75abfc37f4d2b301651
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="enablesharedfromthis-class"></a>enable_shared_from_this — Klasa

Umożliwia generowanie `shared_ptr`.

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

`Ty` Typ kontrolowane przez wskaźnik udostępnionego.

## <a name="remarks"></a>Uwagi

Obiekty pochodne `enable_shared_from_this` można użyć `shared_from_this` metod w funkcji elementów członkowskich, aby utworzyć [shared_ptr](../standard-library/shared-ptr-class.md) właścicieli wystąpienia, które mają prawo własności z istniejącym `shared_ptr` właścicieli. W przeciwnym razie, jeśli tworzysz nową `shared_ptr` za pomocą `this`, jego różni się od istniejącego `shared_ptr` właścicieli, których może prowadzić do nieprawidłowego odwołania lub spowodować, że obiekt ma zostać usunięty w więcej niż raz.

Konstruktory, destruktor i operatora przypisania są chronione ułatwia zapobieganie przypadkowemu nieprawidłowego użycia. Typ argumentu szablonu `Ty` musi być typem klasy pochodnej.

Na przykład użycie zobacz [enable_shared_from_this::shared_from_this](#shared_from_this).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** Standard

## <a name="shared_from_this"></a>  enable_shared_from_this::shared_from_this

Generuje `shared_ptr` który współużytkuje własność wystąpienia z istniejącym `shared_ptr` właścicieli.

```cpp
shared_ptr<T> shared_from_this();
shared_ptr<const T> shared_from_this() const;
```

### <a name="remarks"></a>Uwagi

Jeśli pochodzi obiektów z `enable_shared_from_this` klasa, podstawowa `shared_from_this` szablonu elementu członkowskiego funkcje zwracają [shared_ptr — klasa](../standard-library/shared-ptr-class.md) obiektu, który współużytkuje prawo własności do tego wystąpienia z istniejącym `shared_ptr` właścicieli. W przeciwnym razie, jeśli tworzysz nową `shared_ptr` z `this`, jego różni się od istniejącego `shared_ptr` właścicieli, których może prowadzić do nieprawidłowego odwołania lub spowodować, że obiekt ma zostać usunięty w więcej niż raz. Zachowanie jest niezdefiniowane wywołanie `shared_from_this` w wystąpieniu właścicielem nie jest już `shared_ptr` obiektu.

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