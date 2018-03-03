---
title: Deklaracje i definicje (C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea0f8210993e494cbd4795a2c4cf7c6c0afa8aa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="declarations-and-definitions-c"></a>Deklaracje i definicje (C++)
Deklaracje wprowadzenie nazwy w programie, na przykład nazwy zmiennych, obszary nazw, funkcje i klasy. Deklaracje również określić informacje o typie, a także innych charakterystyk obiekt, który jest został zadeklarowany. Nazwa musi być zadeklarowana przed jej użyciem; w języku C++ punktu, w którym jest zadeklarowany jako nazwę określa, czy jest widoczne dla kompilatora. Nie odwołuje się do funkcji lub klasa, która jest zadeklarowana w pewnym momencie nowsze jednostki kompilacji; można użyć *Przekaż dalej deklaracje* Aby uniknąć problemów tego ograniczenia.  
  
 Definicje Określ, jakie kodu lub danych opisuje nazwę. Kompilator wymaga definicji, aby przydzielić miejsce do magazynowania na rzecz, którą jest on zadeklarowany.  
  
## <a name="declarations"></a>Deklaracje  
 Deklaracja wprowadza jedną lub więcej nazw do programu. Deklaracje może wystąpić więcej niż raz w programie. W związku z tym klasy, struktury, wyliczyć typów, a inne typy danych zdefiniowane przez użytkownika mogą być deklarowane dla każdej jednostki kompilacji. Ograniczenie dla tej deklaracji wielu jest, aby wszystkie deklaracje muszą być takie same. Deklaracje również służyć jako definicje, chyba że deklaracji:  
  
1.  To prototyp funkcji (deklaracji funkcji z treści nie funkcji).  
  
2.  Zawiera `extern` specyfikator, ale inicjator (zmiennych i obiektów) lub treści funkcji (funkcje). To oznacza, że definicja nie jest w bieżącej jednostce tłumaczenia daje połączenie zewnętrzne nazwy.  
  
3.  Jest elementu członkowskiego danych statycznych w deklaracji klasy.  
  
     Klasy statyczne elementy członkowskie danych są współużytkowane przez wszystkie obiekty klasy zmiennych dyskretnych, musi być zdefiniowany i zainicjować poza deklaracją klasy. (Aby uzyskać więcej informacji na temat klas i elementów członkowskich klasy, zobacz [klasy](../cpp/classes-and-structs-cpp.md).)  
  
4.  Jest deklaracji nazwy klasy nie poniższe definicje, takich jak `class T;`.  
  
5.  Jest `typedef` instrukcji.  
  
 Deklaracje, które są również definicje należą:  
  
```  
// Declare and define int variables i and j.  
int i;  
int j = 10;  
  
// Declare enumeration suits.  
enum suits { Spades = 1, Clubs, Hearts, Diamonds };  
  
// Declare class CheckBox.  
class CheckBox : public Control  
{  
public:  
            Boolean IsChecked();  
    virtual int     ChangeState() = 0;  
};  
```  
  
 Niektóre deklaracje, które nie są definicjami są:  
  
```  
  
extern int i;  
char *strchr( const char *Str, const char Target );  
```  
  
 Nazwa jest uważana za zgłaszane, natychmiast po jej deklarator, ale przed jego Inicjator (opcjonalnie). Aby uzyskać więcej informacji, zobacz [punkt deklaracji](../cpp/point-of-declaration-in-cpp.md).  
  
 Deklaracje występują w *zakres*. Zakres kontroluje widoczność zgłoszonej nazwy i ewentualnie czas trwania zdefiniowanego obiektu. Aby uzyskać więcej informacji na temat współdziałania reguły zakresów z deklaracjami, zobacz [zakres](../cpp/scope-visual-cpp.md).  
  
 Deklaracja obiektu jest również definicji, chyba że zawiera on `extern` Specyfikator klasy składującej opisanego w [klasy magazynu](storage-classes-cpp.md). Deklaracja funkcji jest również definicją, chyba że jest prototypem. Prototyp jest nagłówkiem funkcji bez definiowania treści funkcji. Definicja obiektu powoduje alokację pamięci masowej i odpowiednie inicjowania dla tego obiektu.  
  
## <a name="definitions"></a>Definicje  
 Definicja jest unikatowy specyfikacji obiektu lub zmienna, funkcji, klasa lub modułu wyliczającego. Ponieważ definicje musi być unikatowa, program może zawierać tylko jedną definicję dla elementu danego programu. Może istnieć wiele do jednego połączenie między deklaracje i definicje. Istnieją dwa przypadki, w których można zadeklarować i nie zdefiniowano elementu programu:  
  
1.  Funkcja została zadeklarowana, lecz nie istnieje odwołanie z wywołania funkcji lub wyrażenie, które przyjmuje adresu funkcji.  
  
2.  Klasa jest używana tylko w taki sposób, który nie wymaga jego definicji być znane. Jednak klasy musi być zadeklarowany. Poniższy kod ilustruje w takim przypadku:  
  
    ```  
    // definitions.cpp  
    class WindowCounter;   // Forward declaration; no definition  
  
    class Window  
    {  
       // Definition of WindowCounter not required  
       static WindowCounter windowCounter;  
    };  
  
    int main()  
    {  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)   
 [Punkt deklaracji](../cpp/point-of-declaration-in-cpp.md)