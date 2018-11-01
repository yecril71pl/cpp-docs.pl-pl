---
title: type_info — Klasa
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 169a54373c66c2f6b33d71e68500c3bf85e871c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560722"
---
# <a name="typeinfo-class"></a>type_info — Klasa

**Type_info** klasa opisuje typ informacji generowanych w programie przez kompilator. Obiekty tej klasy skutecznie przechowują wskaźnik do nazwy typu. **Type_info** Klasa zapisuje również zakodowaną wartość odpowiednią do porównywania dwóch typów dla równości lub kolejności sortowania. Reguły kodowania i sekwencja typów sortowania są nieokreślone i mogą się różnić między programami.

`<typeinfo>` Plik nagłówka musi być uwzględniony, aby można było używać **type_info** klasy. Interfejs **type_info** klasa jest:

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

Nie można utworzyć wystąpienia obiektów **type_info** klasy bezpośrednio, ponieważ klasa ma Konstruktor kopii prywatnej. Jedynym sposobem, aby skonstruować (tymczasowo) **type_info** obiektu jest użycie [typeid](../cpp/typeid-operator.md) operatora. Ponieważ operator przypisania jest również prywatny, nie można kopiować lub przypisywać obiektów klasy **type_info**.

`type_info::hash_code` definiuje funkcję mieszania odpowiednią do mapowania wartości typu **typeinfo** do rozłożenia wartości indeksu.

Operatory `==` i `!=` może służyć do porównywania równości i nierówności z innymi **type_info** obiektów, odpowiednio.

Nie ma żadnego połączenia między określoną kolejnością typów i relacjami dziedziczenia. Użyj `type_info::before` funkcja elementu członkowskiego, aby określić kolejność sortowania typów. Nie ma żadnej gwarancji, `type_info::before` da ten sam wynik w różnych programach lub nawet cyklach tego samego programu. W ten sposób `type_info::before` przypomina address-of `(&)` operatora.

`type_info::name` Funkcja elementu członkowskiego zwraca `const char*` na ciąg zakończony znakiem null, reprezentujący zrozumiałą nazwę typu. Wskazywana pamięć jest buforowana i nigdy nie powinna być bezpośrednio dealokowana.

`type_info::raw_name` Funkcja elementu członkowskiego zwraca `const char*` na ciąg zakończony znakiem null, który reprezentuje dekorowaną nazwę typu obiektu. Nazwa rzeczywiście jest przechowywana w formie urządzonej, aby zaoszczędzić miejsce. W związku z tym, ta funkcja jest szybsza niż `type_info::name` , ponieważ nie trzeba unikać oszczędzania nazwy. Ciąg zwracany przez `type_info::raw_name` funkcji jest przydatny w operacjach porównania, ale nie jest czytelny. Ciąg czytelny dla człowieka, należy użyć `type_info::name` zamiast tego funkcji.

Informacje o typie jest generowana dla polimorficznych klas tylko wtedy, gdy [/GR (Włącz Run-Time informacje o typie)](../build/reference/gr-enable-run-time-type-information.md) określono opcję kompilatora.

## <a name="see-also"></a>Zobacz także

[Informacje o typach uzyskiwane w czasie rzeczywistym](../cpp/run-time-type-information.md)