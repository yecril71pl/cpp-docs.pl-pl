---
title: właściwości (C + +/ CLI i C + +/ CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- property_cpp
- property
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
ms.openlocfilehash: 31b5673426a8c31cea203002018cc3a465952859
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787155"
---
# <a name="property--ccli-and-ccx"></a>właściwości (C + +/ CLI i C + +/ CX)

Deklaruje *właściwość*, która jest funkcją składową, który zachowuje się i jest dostępny, takich jak element członkowski danych lub element tablicy.

## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze

Można zadeklarować jedną z następujących typów właściwości.

*właściwości prostej*<br/>
Domyślnie tworzy *ustawiająca metoda dostępu* , przypisuje wartość właściwości *pobierająca* , który pobiera wartość właściwości oraz element członkowski danych prywatnych generowanych przez kompilator, który zawiera wartość właściwości.

*Blok właściwości*<br/>
Umożliwia tworzenie get zdefiniowanych przez użytkownika i/lub ustaw metody dostępu. Właściwość jest odczytu/zapisu, jeśli obie opcje pobierania i metody dostępu set są zdefiniowane, tylko do odczytu, jeśli tylko zdefiniowano metody dostępu get i tylko do zapisu czy tylko metody dostępu set jest zdefiniowana.

Należy jawnie deklarować element członkowski danych zawiera wartość właściwości.

*Właściwość indeksowana*<br/>
Blok właściwości, który służy do pobierania i ustawiania wartości właściwości, która jest określona przez jednego lub kilku indeksów.

Właściwość indeksowana, który ma uprawnienia można utworzyć nazwy właściwości zdefiniowanych przez użytkownika lub *domyślne* nazwy właściwości. Nazwa domyślnej właściwości indeksu jest nazwa klasy, w którym właściwość jest zdefiniowana. Aby zadeklarować właściwość domyślną, określić **domyślne** słowa kluczowego zamiast nazwy właściwości.

Należy jawnie deklarować element członkowski danych zawiera wartość właściwości. Właściwości indeksowane element członkowski danych jest zazwyczaj tablicy lub kolekcji.

### <a name="syntax"></a>Składnia

```cpp
property type property_name;

property type property_name {
   access-modifier type get() inheritance-modifier {property_body};
   access-modifier void set(type value) inheritance-modifier {property_body};
}

property type property_name[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}

property type default[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}
```

### <a name="parameters"></a>Parametry

*type*<br/>
Typ danych wartości właściwości i samej właściwości.

*property_name*<br/>
Nazwa właściwości.

*access-modifier*<br/>
Kwalifikator dostępu. Prawidłowy kwalifikatory to **statyczne** i **wirtualnego**.

Get lub metody dostępu set nie muszą uzgodnić **wirtualnego** kwalifikator, ale musisz wyrazić zgodę na **statyczne** kwalifikator.

*inheritance-modifier*<br/>
Kwalifikator dziedziczenia. Prawidłowy kwalifikatory to **abstrakcyjne** i **zapieczętowanego**.

*index_list*<br/>
Rozdzielana przecinkami lista jednego lub kilku indeksów. Każdy indeks zawiera typ indeksu i opcjonalny identyfikator, który może służyć w treści metody właściwości.

*value*<br/>
Wartość do przypisania do właściwości w operacji zestawu, lub pobrać w ramach operacji get.

*property_body*<br/>
Właściwości treści metody dostępu set lub get. *Property_body* służy *index_list* dostęp podstawowego elementu danych właściwości do lub jako parametry podczas przetwarzania zdefiniowanych przez użytkownika.

## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows

Aby uzyskać więcej informacji, zobacz [właściwości (C + +/ CX)](https://msdn.microsoft.com/library/windows/apps/hh755807.aspx).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/ZW`

## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania

### <a name="syntax"></a>Składnia

```cpp
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}
```

### <a name="parameters"></a>Parametry

*modifier*<br/>
Modyfikatory, które mogą być używane w deklaracji właściwości lub metody dostępu get/set. Możliwe wartości to **statyczne** i **wirtualnego**.

*type*<br/>
Typ wartości, który jest reprezentowany przez właściwość.

*property_name*<br/>
Parametry metody Zgłoś; musi odpowiadać podpisowi delegata.

*index_list*<br/>
Rozdzielana przecinkami lista jednego lub kilku indeksów, określone w nawiasach kwadratowych (operator indeksu dolnego, ([])). Dla każdego indeksu należy określić typ i opcjonalnie identyfikator, który może służyć w treści metody właściwości.

### <a name="remarks"></a>Uwagi

W pierwszym przykładzie pokazano składnię *właściwości prostej*, która niejawnie deklaruje zarówno `set` i `get` metody. Kompilator automatycznie tworzy prywatnego pola do przechowywania wartości właściwości.

W drugim przykładzie pokazano składni *blok właściwości*, która deklaruje jawnie zarówno `set` i `get` metody.

Trzeci przykład składni pokazuje, zdefiniowaną przez użytkownika *index — właściwość*. Właściwości indeksu przyjmuje parametry oprócz wartość można ustawić lub pobrać. Należy określić nazwę właściwości. W odróżnieniu od właściwości prostej `set` i/lub `get` metody, właściwości indeksu musi być jawnie zdefiniowany. Ponadto należy określić nazwę właściwości.

W przykładzie pokazano składnię czwarty *domyślne* właściwość, która zapewnia dostęp tablicy do wystąpienia tego typu. Słowo kluczowe **domyślne**, służy tylko do określenia właściwości domyślnej. Nazwa właściwości domyślnej jest nazwa typu, w którym właściwość jest zdefiniowana.

**Właściwość** — słowo kluczowe może występować w klasą, interfejsem lub typu wartości. Właściwość może mieć funkcję get (tylko do odczytu), funkcja set (tylko do zapisu) lub obu (odczyt zapis).

Nazwa właściwości nie może odpowiadać nazwie klasy zarządzanej, która go zawiera. Zwracany typ funkcji pobierającej musi odpowiadać typowi ostatniego parametru funkcji odpowiedniej metody ustawiającej.

Dla kodu klienta właściwość wygląd element członkowski danych zwykłe i można można zapisane lub odczytywać przy użyciu tej samej składni jak element członkowski danych.

Get i metody set nie muszą uzgodnić **wirtualnego** modyfikator.

Dostępność metody get i set, metoda może się różnić.

Definicja metody właściwości mogą być wyświetlane poza treścią klasy, podobnie jak zwykłej metody.

Get i metody set dla właściwości uzgadniają **statyczne** modyfikator.

Właściwość jest skalarna jeśli jego get i zestaw metod dopasowania następujący opis:

- Metoda get nie ma parametrów, a ma typ zwracany `T`.

- Metoda set ma parametr typu `T`, a zwracany typ **void**.

Powinna istnieć tylko jedna właściwość skalarną zadeklarowana w zakresie za pomocą tego samego identyfikatora. Właściwości skalarne nie mogą być przeciążone.

Gdy element członkowski danych właściwości jest zadeklarowany, kompilator wprowadza element członkowski danych — czasami określane jako "magazyn zapasowy" — w klasie. Nazwa elementu członkowskiego danych jest jednak formularza tak, aby tak, jakby był to element członkowski danych rzeczywistych zawierającego klasy nie może odwoływać się elementu członkowskiego w źródle. Użyj ildasm.exe, aby wyświetlić metadane dla danego typu i sprawdzić nazwę właściwości zapasowy magazyn generowanych przez kompilator.

Różnej dostępności jest dozwolony dla metod dostępu w bloku właściwości.  Oznacza to, że metoda zestawu może być publiczny i metody get może być prywatny.  Jednak występuje błąd dla metody dostępu w celu mieć mniej restrykcyjny dostępność niż w deklaracji samej właściwości.

**Właściwość** jest kontekstowej słowem kluczowym.  Aby uzyskać więcej informacji, zobacz [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md).

### <a name="requirements"></a>Wymagania

— Opcja kompilatora: `/clr`

### <a name="examples"></a>Przykłady

Poniższy przykład przedstawia deklarację i korzystanie z właściwości składowej danych i w bloku właściwości.  Pokazuje również, że metoda dostępu do właściwości mogą być definiowane poza klasy.

```cpp
// mcppv2_property.cpp
// compile with: /clr
using namespace System;
public ref class C {
   int MyInt;
public:

   // property data member
   property String ^ Simple_Property;

   // property block
   property int Property_Block {

      int get();

      void set(int value) {
         MyInt = value;
      }
   }
};

int C::Property_Block::get() {
   return MyInt;
}

int main() {
   C ^ MyC = gcnew C();
   MyC->Simple_Property = "test";
   Console::WriteLine(MyC->Simple_Property);

   MyC->Property_Block = 21;
   Console::WriteLine(MyC->Property_Block);
}
```

```Output
test

21
```

## <a name="see-also"></a>Zobacz też

[Rozszerzenia składników dla platformy .NET i platformy uniwersalnej systemu Windows](component-extensions-for-runtime-platforms.md)