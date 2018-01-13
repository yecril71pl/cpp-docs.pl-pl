---
title: "Tworzenie manipulatorów bez argumentów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: manipulators
ms.assetid: 2dc62d09-45b7-454d-bd9d-55f3c72c206d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c7439908970d61f55f10915ff69bc990a6fcc841
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="writing-your-own-manipulators-without-arguments"></a>Tworzenie manipulatorów bez argumentów
Pisanie manipulatory, które nie korzystają z argumentami wymaga pochodnym klasy ani użycie makra złożonych. Załóżmy, że drukarka wymaga pary \<ESC > [Aby przejść do trybu pogrubione. Możesz wstawić tej pary bezpośrednio do strumienia:  
  
```  
cout <<"regular " <<'\033' <<'[' <<"boldface" <<endl;  
```  
  
 Czy można określić `bold` manipulatora, która wstawia znaki:  
  
```  
ostream& bold(ostream& os) {  
    return os <<'\033' <<'[';  
}  
cout <<"regular " <<bold <<"boldface" <<endl;  
```  
  
 Globalny zdefiniowanych `bold` funkcja przyjmuje `ostream` odwołania argument i zwraca `ostream` odwołania. Nie jest funkcją członkowską lub znajomego ponieważ nie potrzebuje dostępu do elementów Klasa prywatna. `bold` Funkcja łączy do strumienia, ponieważ strumień `<<` operator jest przeciążony zaakceptować tego typu funkcji, za pomocą deklaracji, która wygląda następująco:  
  
```  
_Myt& operator<<(ios_base& (__cdecl *_Pfn)(ios_base&))  
{     // call ios_base manipulator  
 (*_Pfn)(*(ios_base *)this);

    return (*this);

}  
```  
  
 Ta funkcja umożliwia rozszerzanie innych przeciążone operatory. W takim przypadku jest przypadkowe który `bold` wstawia znaków do strumienia. Funkcja jest wywoływana po wstawieniu do strumienia, niekoniecznie wydrukowaniu sąsiadujących ze sobą znaków. W związku z tym drukowanie może być opóźniony ze względu na buforowanie strumienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Strumienie wyjściowe](../standard-library/output-streams.md)

