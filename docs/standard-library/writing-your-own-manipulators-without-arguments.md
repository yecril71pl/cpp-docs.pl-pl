---
title: Tworzenie manipulatorów bez argumentów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: df8fcc1f316b5281e8c6775492d402559d77f483
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Tworzenie manipulatorów bez argumentów

Pisanie manipulatory, które nie korzystają z argumentami wymaga pochodnym klasy ani użycie makra złożonych. Załóżmy, że drukarka wymaga pary \<ESC > [Aby przejść do trybu pogrubione. Możesz wstawić tej pary bezpośrednio do strumienia:

```cpp
cout <<"regular " <<'\033' <<'[' <<"boldface" <<endl;
```

Czy można określić `bold` manipulatora, która wstawia znaki:

```cpp
ostream& bold(ostream& os) {
    return os <<'\033' <<'[';
}
cout <<"regular " <<bold <<"boldface" <<endl;
```

Globalny zdefiniowanych `bold` funkcja przyjmuje `ostream` odwołania argument i zwraca `ostream` odwołania. Nie jest funkcją członkowską lub znajomego ponieważ nie potrzebuje dostępu do elementów Klasa prywatna. `bold` Funkcja łączy do strumienia, ponieważ strumień `<<` operator jest przeciążony zaakceptować tego typu funkcji, za pomocą deklaracji, która wygląda następująco:

```cpp
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))
{     // call ios_base manipulator
 (*_Pfn)(*(ios_base *)this);

    return (*this);

}
```

Ta funkcja umożliwia rozszerzanie innych przeciążone operatory. W takim przypadku jest przypadkowe który `bold` wstawia znaków do strumienia. Funkcja jest wywoływana po wstawieniu do strumienia, niekoniecznie wydrukowaniu sąsiadujących ze sobą znaków. W związku z tym drukowanie może być opóźniony ze względu na buforowanie strumienia.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
