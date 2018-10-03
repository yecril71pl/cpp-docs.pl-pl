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
ms.openlocfilehash: e8bfad1919863a58554604fe6d32b4563e57a14a
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235714"
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Tworzenie manipulatorów bez argumentów

Zapisywanie manipulatory, które nie korzystają z argumentami wymaga pochodnym klasy ani złożone makra używane. Załóżmy, że drukarka wymaga pary \<ESC > [tak, aby przejść do trybu pogrubienie. Ta para można wstawić bezpośrednio do strumienia:

```cpp
cout << "regular " << '\033' << '[' << "boldface" << endl;
```

Lub można zdefiniować `bold` manipulator, który wstawia znaki:

```cpp
ostream& bold(ostream& os) {
    return os << '\033' << '[';
}
cout << "regular " << bold << "boldface" << endl;
```

Globalnie zdefiniowanych `bold` funkcja przyjmuje `ostream` odwoływać się do argumentu i zwraca `ostream` odwołania. Nie jest funkcją składową lub znajomego, ponieważ nie wymaga dostępu do żadnych elementów Klasa prywatna. `bold` Funkcja łączy do strumienia, ponieważ strumień `<<` operator jest przeciążony do akceptowania tego typu funkcji, za pomocą deklaracji, która wygląda mniej więcej tak:

```cpp
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))
{
    // call ios_base manipulator
    (*_Pfn)(*(ios_base *)this);

    return (*this);
}
```

Ta funkcja umożliwia rozszerzanie innych przeciążonych operatorów. W tym przypadku jest też przypadkowe, `bold` wstawia znaki do strumienia. Funkcja jest wywoływana, gdy go jest wstawiany do strumienia, niekoniecznie drukowaniu sąsiadujących znaków. W związku z tym drukowanie, może być opóźniony ze względu na buforowanie strumienia.

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
