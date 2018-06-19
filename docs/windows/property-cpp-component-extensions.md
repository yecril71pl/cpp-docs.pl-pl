---
title: właściwości (C++ Component Extensions) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- property_cpp
- property
dev_langs:
- C++
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b763131fe91e2df2385f2c06bcba8bc759d695a1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882709"
---
# <a name="property--c-component-extensions"></a>property (C++ Component Extensions)
Deklaruje *właściwość*, która jest funkcją członkowską, który zachowuje się oraz uzyskiwania dostępu do elementu członkowskiego danych lub element tablicy.  
  
## <a name="all-runtimes"></a>Wszystkie środowiska wykonawcze  
 Można zadeklarować jedną z następujących typów właściwości.  
  
 *właściwości prostej*  
 Domyślnie tworzy *akcesor zestawu* która przypisuje wartość właściwości *Uzyskaj dostęp* , który pobiera wartość właściwości i elementu członkowskiego danych prywatnych generowane przez kompilator, który zawiera wartość właściwości.  
  
 *Właściwość bloku*  
 Służy do tworzenia get zdefiniowane przez użytkownika i/lub metod dostępu set. Ta właściwość jest odczytu/zapisu, jeśli obie get i metody dostępu set są zdefiniowane, tylko do odczytu, jeśli tylko metody dostępu get jest zdefiniowany i tylko do zapisu, jeśli tylko metody dostępu set jest zdefiniowany.  
  
 Musisz jawnie zadeklarować elementu członkowskiego danych zawiera wartość właściwości.  
  
 *Właściwości indeksowane*  
 Bloku właściwości, używanej do pobierania i ustawiania wartości właściwości, która jest określana przez jednego lub kilku indeksów.  
  
 Można utworzyć właściwości indeksowanej ma jedną nazwę właściwości zdefiniowane przez użytkownika lub *domyślne* nazwy właściwości. Nazwa domyślnej właściwości indeksu jest nazwa klasy, w którym właściwość jest zdefiniowana. Aby zadeklarować właściwości domyślnej, należy określić `default` słowa kluczowego zamiast nazwy właściwości.  
  
 Musisz jawnie zadeklarować elementu członkowskiego danych zawiera wartość właściwości. Właściwości indeksowane element członkowski danych jest zwykle tablicy lub kolekcji.  
  
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
 `type`  
 Typ danych wartości właściwości i samej właściwości.  
  
 `property_name`  
 Nazwa właściwości.  
  
 `access-modifier`  
 Kwalifikator dostępu. Nieprawidłowa kwalifikatory są `static` i `virtual`.  
  
 Get lub metody dostępu set nie należy uzgodnić `virtual` kwalifikator, ale należy uzgodnić `static` kwalifikatora.  
  
 `inheritance-modifier`  
 Kwalifikator dziedziczenia. Nieprawidłowa kwalifikatory są `abstract` i `sealed`.  
  
 `index_list`  
 Rozdzielana przecinkami lista jednego lub kilku indeksów. Każdy indeks obejmuje typ indeksu i opcjonalny identyfikator, który może być używana w treści metody właściwości.  
  
 `value`  
 Wartość do przypisania do właściwości w operacji set lub pobrać w operacji get.  
  
 `property_body`  
 Treść metody właściwości metody dostępu set lub get. `property_body` Można użyć `index_list` uzyskać dostępu do właściwości członka danych podstawowej, lub jako parametry w przetwarzaniu zdefiniowane przez użytkownika.  
  
## <a name="windows-runtime"></a>Środowisko wykonawcze systemu Windows  
 Aby uzyskać więcej informacji, zobacz [właściwości (C + +/ CX)](http://msdn.microsoft.com/library/windows/apps/hh755807.aspx).  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora: **/ZW**  
  
## <a name="common-language-runtime"></a>środowiska uruchomieniowe w trakcie wykonania 
 **Składnia**  
  
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
  
 **Parametry**  
  
 *Modyfikator*  
 Modyfikator, które mogą być używane w deklaracji właściwości lub metody dostępu get/set. Możliwe wartości to `static` i `virtual`.  
  
 *Typ*  
 Typ wartości, który jest reprezentowany przez właściwość.  
  
 *Property_Name*  
 Parametry dla metody Zgłoś; musi być zgodna podpis delegata.  
  
 *index_list*  
 Rozdzielana przecinkami lista jednego lub kilku indeksów, określona w nawiasach kwadratowych (operator indeksu dolnego, ([])). Dla każdego indeksu Określ typ i opcjonalnie identyfikatora, który może służyć w treści metody właściwości.  
  
 **Uwagi**  
  
 W pierwszym przykładzie składni *właściwości prostej*, która niejawnie deklaruje element zarówno `set` i `get` metody. Kompilator automatycznie tworzy pole prywatne do przechowywania wartości właściwości.  
  
 W drugim przykładzie składni *bloku właściwości*, który deklaruje jawnie zarówno `set` i `get` metody.  
  
 W trzecim składni przykładzie zdefiniowany przez klienta *właściwość indeksu*. Właściwości indeksu przyjmuje parametry oprócz wartość można ustawić ani pobrać. Należy określić nazwę właściwości. W odróżnieniu od właściwości prostej `set` i/lub `get` metody właściwości indeksu musi być jawnie zdefiniowany i należy określić nazwę właściwości.  
  
 W przykładzie przedstawiono składnię czwarty *domyślne* właściwość, która zapewnia dostęp tablicy do wystąpienia typu. Słowo kluczowe `default`, służy tylko do określenia domyślnej właściwości. Nazwa właściwości domyślnej jest nazwa typu, w którym właściwość jest zdefiniowana.  
  
 `property` — Słowo kluczowe może występować w klasą, interfejsem lub typem wartości. Właściwości może mieć funkcję get (tylko do odczytu), funkcji zestawu (tylko do zapisu) lub obu (odczytu i zapisu).  
  
 Nazwa właściwości nie może odpowiadać nazwie zarządzanej klasy, która go zawiera. Zwracany typ funkcji pobierającej musi odpowiadać typowi ostatniego parametru funkcji odpowiedniej metody ustawiającej.  
  
 Do kodu klienta właściwość ma wygląd elementu członkowskiego danych zwykłej i może być zapisywania lub odczytywania z przy użyciu takiej samej składni jako element członkowski danych.  
  
 Pobierz i metody set nie należy uzgodnić `virtual` modyfikator.  
  
 Dostępność elementu get i set, metoda może się różnić.  
  
 Definicja metody property może występować poza ciałem klasy, podobnie jak w zwykłym — metoda.  
  
 Get i set, metoda właściwości uzgadnia **statycznych** modyfikator.  
  
 Właściwość jest skalarny jeśli jego get metody set mieści się następujący opis:  
  
-   Metoda get nie ma parametrów, a ma typ zwracany `T`.  
  
-   Metoda set ma parametr typu `T`i typ zwracany **void**.  
  
 Muszą istnieć tylko jedna właściwość skalarna zadeklarowana w zakresie o tym samym identyfikatorze. Właściwości skalarne nie może być przeciążony.  
  
 Gdy właściwość elementu członkowskiego danych jest zadeklarowany, kompilator injects elementu członkowskiego danych — czasami określane jako "magazynu zapasowego" — w klasie. Nazwa elementu członkowskiego danych jest jednak formularza tak, aby tak, jakby był on elementu członkowskiego danych rzeczywistych zawierające klasy nie może odwoływać się element członkowski w źródle. Ildasm.exe umożliwia wyświetlenie metadanych dla danego typu oraz nazwę magazynu zapasowego właściwości generowane przez kompilator.  
  
 Ułatwienia dostępu w różnych jest dozwolony dla metod dostępu w bloku właściwości.  Oznacza to set, metoda może być publiczny i metody get mogą być prywatne.  Jednak jest błąd dla metody dostępu ma mniej restrykcyjną ułatwień dostępu, niż jest to w deklaracji samej właściwości.  
  
 `property` jest słowem kluczowym kontekstowa.  Aby uzyskać więcej informacji, zobacz [słowa kluczowe Context-Sensitive](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
  
### <a name="requirements"></a>Wymagania  
 — Opcja kompilatora:   **/CLR**  
  
### <a name="examples"></a>Przykłady  
 W poniższym przykładzie przedstawiono deklaracji i korzystanie z właściwości elementu członkowskiego danych i bloku właściwości.  Pokazuje też, że akcesor właściwości mogą być definiowane poza klasy.  
  
```  
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
  
 **Output**  
  
```Output  
test  
  
21  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)