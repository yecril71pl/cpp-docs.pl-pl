---
title: "type_info — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_info
dev_langs: C++
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9cd5a1844bfeec798ee25a3cb8e65efd019e65e9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="typeinfo-class"></a>type_info — Klasa
**Type_info —** klasa opisuje informacje o typie w program generowane przez kompilator. Obiekty tej klasy skutecznie przechowują wskaźnik do nazwy typu. **Type_info —** klasy przechowuje także zakodowaną wartość odpowiednie do porównywania dwóch typów równości lub kolejności sortowania. Reguły kodowania i sekwencja typów sortowania są nieokreślone i mogą się różnić między programami.  
  
 `<typeinfo>` Pliku nagłówka musi być uwzględniony, aby można było używać **type_info —** klasy. Interfejs dla **type_info —** klasa jest:  
  
```cpp
class type_info {  
public:  
    virtual ~type_info();  
    size_t hash_code() const  
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;  
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;  
    _CRTIMP_PURE int before(const type_info& rhs) const;  
    _CRTIMP_PURE const char* name() const;  
    _CRTIMP_PURE const char* raw_name() const;  
};  
```  
  
 Nie można utworzyć wystąpienia obiektów **type_info —** klasy bezpośrednio, ponieważ klasa ma tylko konstruktora kopiującego prywatnych. Jedynym sposobem, aby utworzyć (tymczasowe) **type_info —** obiektu jest użycie [typeid](../cpp/typeid-operator.md) operatora. Operator przypisania również jest prywatny, nie można skopiować lub przypisać obiektów klasy **type_info —**.  
  
 **type_info::hash_code** definiuje odpowiedni w przypadku mapowania wartości typu funkcji skrótu **typeinfo** dystrybucji wartości indeksu.  
  
 Operatory `==` i `!=` może służyć do porównania równości i nierówności z innymi **type_info —** obiekty odpowiednio.  
  
 Nie ma żadnego połączenia między określoną kolejnością typów i relacjami dziedziczenia. Użyj **type_info::before** funkcji członkowskiej, aby określić kolejność sortowania typów. Nie ma żadnych gwarancji, że **type_info::before** umożliwia uzyskanie takiego samego wyniku w różnych programów lub nawet innej serii ten sam program. W ten sposób **type_info::before** jest podobny do adresu z **(&)** operatora.  
  
 **Type_info::name** zwraca funkcja członkowska **const char\***  do zerem ciąg reprezentujący czytelną nazwę typu. Wskazywana pamięć jest buforowana i nigdy nie powinna być bezpośrednio dealokowana.  
  
 **Type_info::raw_name** zwraca funkcja członkowska **const char\***  do zerem ciąg reprezentujący nazwę ozdobione typu obiektu. Nazwa rzeczywiście jest przechowywana w formie urządzonej, aby zaoszczędzić miejsce. W związku z tym, ta funkcja jest szybsza niż **type_info::name** , ponieważ nie trzeba undecorate nazwy. Długość ciągu zwróconego przez **type_info::raw_name** funkcja jest przydatna podczas wykonywania operacji porównania, ale nie jest do odczytu. Ciąg zrozumiałą dla użytkownika, należy użyć **type_info::name** zamiast tego działania.  
  
 Informacje o typie jest generowane dla klasy polimorficzne tylko wtedy, gdy [/GR (Włącz Run-Time informacji o typie)](../build/reference/gr-enable-run-time-type-information.md) określono opcję kompilatora.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o typach uzyskiwane w czasie rzeczywistym](../cpp/run-time-type-information.md)
