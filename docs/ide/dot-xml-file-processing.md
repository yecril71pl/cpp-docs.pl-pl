---
title: . Przetwarzanie pliku XML | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- XML documentation, processing XML file
ms.assetid: e70fdeae-80ac-4872-ab24-771c5635cfbf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1cf6f5660e1aaeaeff4050bb80009eda7d14c3ba
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340518"
---
# <a name="xml-file-processing"></a>Przetwarzanie pliku .Xml
Kompilator generuje ciąg Identyfikatora dla każdego konstrukcji w kodzie zostanie oznaczony do generowania dokumentacji. Aby uzyskać więcej informacji, zobacz [zalecane znaczniki komentarzy dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md). Ciąg Identyfikatora unikatowo identyfikuje konstrukcja. Programów, które przetwarzają pliku XML, który umożliwia Zidentyfikuj odpowiednie środowiska .NET Framework metadane lub odbicia element dotyczy dokumentacji ciąg Identyfikatora.  
  
 Plik XML nie jest hierarchiczną reprezentację kodu, jest płaska lista z Identyfikatorem wygenerowany dla każdego elementu.  
  
 Kompilator stosuje następujące reguły podczas generowania ciągi identyfikatorów:  
  
-   Nie biały znak jest umieszczona w ciągu.  
  
-   Pierwsza część ciąg Identyfikatora określa rodzaj elementu członkowskiego jest określony, z jednego znaku z dwukropkiem. Używane są następujące typy elementu członkowskiego:  
  
    |Znak|Opis|  
    |---------------|-----------------|  
    |N|— przestrzeń nazw<br /><br /> Nie można dodać komentarze dokumentacji do przestrzeni nazw, możliwe cref odwołania do przestrzeni nazw.|  
    |T|Typ: klasy, interfejsu, struktury, wyliczenia, delegata|  
    |D|— klasa typedef|  
    |F|pole|  
    |P|właściwości (łącznie z indeksatorów i inne właściwości indeksowane)|  
    |M|(w tym takie specjalne metody jako konstruktorów, Operatorzy i tak dalej) — metoda|  
    |E|zdarzenie|  
    |!|Ciąg błędu<br /><br /> Pozostała część ciągu zawiera informacje o tym błędzie. Kompilator Visual C++ generuje informacje o błędzie dla łącza, które nie zostały rozpoznane.|  
  
-   Druga część ciągu jest w pełni kwalifikowana nazwa elementu, zaczynając od katalogu głównego przestrzeni nazw. Nazwa elementu, jego otaczającego typ lub typy i przestrzeni nazw są oddzielone kropkami. Jeśli nazwa elementu zawiera okresów, są one zastąpione kratki (#). Zakłada się, że żadne pozycje nie kratki bezpośrednio w swoim imieniu. Na przykład w pełni kwalifikowana nazwa `String` Konstruktor może być "System.String.#ctor".  
  
-   Dla właściwości i metody w przypadku argumentów dla metody, ujęte w nawiasy listy argumentów jest zgodna. Jeśli nie ma żadnych argumentów, nawiasów, nie są dostępne. Argumenty są oddzielone przecinkami. Kodowanie każdy argument następujące bezpośrednio, jak jest zakodowany w podpisie .NET Framework:  
  
    -   Typy podstawowe. Typy regularne (po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE) są reprezentowane jako w pełni kwalifikowana nazwa typu.  
  
    -   Typy wewnętrzne (na przykład ELEMENT_TYPE_I4, ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. i ELEMENT_TYPE_VOID) są reprezentowane jako pełni kwalifikowana nazwa typu odpowiadającego pełne, na przykład **System.Int32** lub **System.TypedReference**.  
  
    -   Poprawności elementu ELEMENT_TYPE_PTR jest reprezentowany jako ' *' następujące zmodyfikowanej typu.  
  
    -   ELEMENT_TYPE_BYREF jest reprezentowany jako "\@" następujące zmodyfikowanej typu.  
  
    -   ELEMENT_TYPE_PINNED jest reprezentowany jako "^" następujące zmodyfikowanej typu. Kompilator Visual C++ nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_CMOD_REQ jest reprezentowany jako "&#124;" i w pełni kwalifikowaną nazwę klasy modyfikator, po modyfikacji typu. Kompilator Visual C++ nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_CMOD_OPT jest reprezentowany jako "!" i w pełni kwalifikowaną nazwę klasy modyfikator, po modyfikacji typu.  
  
    -   ELEMENT_TYPE_SZARRAY jest reprezentowany jako [następującego typu elementu tablicy "]".  
  
    -   ELEMENT_TYPE_GENERICARRAY jest reprezentowany jako "[?]" następującego typu elementu tablicy. Kompilator Visual C++ nigdy nie generuje to.  
  
    -   ELEMENT_TYPE_ARRAY jest reprezentowany jako [*ich*:`size`,*ich*:`size`] liczba przecinkami w przypadku rangę - 1 oraz dolną granicę i rozmiar każdego wymiaru, jeśli znane są reprezentowane w dziesiętnych. Jeśli nie określono dolną granicę lub rozmiar, po prostu zostanie pominięty. Jeśli pominięto dolna granica i rozmiaru dla określonego wymiaru ":" zostanie pominięty również. Na przykład 2-wymiarową tablicą o 1 jako nieokreślony rozmiary i dolne granice tablicy to [1:, 1:].  
  
    -   ELEMENT_TYPE_FNPTR jest reprezentowany jako "= FUNC:`type`(*podpisu*)", gdzie `type` jest zwracany typ i *podpisu* jest argumenty metody. Jeśli nie ma żadnych argumentów, nawiasy są pomijane. Kompilator Visual C++ nigdy nie generuje to.  
  
     Następujące składniki podpisu nie są reprezentowane, ponieważ nigdy nie są używane dla różnego przeciążonych metod:  
  
    -   Konwencja wywoływania  
  
    -   Zwracany typ  
  
    -   ELEMENT ELEMENT_TYPE_SENTINEL  
  
-   Tylko operatory konwersji, aby uzyskać wartość zwracaną przez metodę został zakodowany jako "~" następuje zwracany typ wcześniej zakodowany.  
  
-   Dla typów ogólnych Nazwa typu będzie następować wstecz znaczników, a następnie liczbę wskazującą liczbę parametrów typu ogólnego.  Na przykład  
  
    ```  
    <member name="T:MyClass`2">  
    ```  
  
     Dla typu, który jest zdefiniowany jako `public class MyClass<T, U>`.  
  
     Dla metod biorąc typów podstawowych jako parametrów, parametry typu ogólnego są określone jako liczby poprzedzone znakiem Takty Wstecz (na przykład \`0, \`1).  Każdy liczba reprezentująca liczony od zera tablicy notacji ogólnych parametrów typu.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano, jak identyfikator ciągi dla klasy i jej elementów członkowskich powinien zostać wygenerowany.  
  
```  
// xml_id_strings.cpp  
// compile with: /clr /doc /LD  
///   
namespace N {    
// "N:N"  
  
   /// <see cref="System" />  
   //  <see cref="N:System"/>  
   ref class X {      
   // "T:N.X"  
  
   protected:  
      ///   
      !X(){}     
      // "M:N.X.Finalize", destructor's representation in metadata  
  
   public:  
      ///   
      X() {}     
      // "M:N.X.#ctor"  
  
      ///   
      static X() {}     
      // "M:N.X.#cctor"  
  
      ///   
      X(int i) {}     
      // "M:N.X.#ctor(System.Int32)"  
  
      ///   
      ~X() {}     
      // "M:N.X.Dispose", Dispose function representation in metadata  
  
      ///   
      System::String^ q;     
      // "F:N.X.q"  
  
      ///   
      double PI;     
      // "F:N.X.PI"  
  
      ///   
      int f() { return 1; }     
      // "M:N.X.f"  
  
      ///   
      int bb(System::String ^ s, int % y, void * z) { return 1; }  
      // "M:N.X.bb(System.String,System.Int32@,System.Void*)"  
  
      ///   
      int gg(array<short> ^ array1, array< int, 2 >^ IntArray) { return 0; }   
      // "M:N.X.gg(System.Int16[], System.Int32[0:,0:])"  
  
      ///   
      static X^ operator+(X^ x, X^ xx) { return x; }  
     // "M:N.X.op_Addition(N.X,N.X)"  
  
      ///   
      property int prop;     
      // "M:N.X.prop"  
  
      ///   
      property int prop2 {     
      // "P:N.X.prop2"  
  
         ///   
         int get() { return 0; }  
         // M:N.X.get_prop2  
  
         ///   
         void set(int i) {}  
         // M:N.X.set_prop2(System.Int32)  
      }  
  
      ///   
      delegate void D(int i);   
      // "T:N.X.D"  
  
      ///   
      event D ^ d;   
      // "E:N.X.d"  
  
      ///   
      ref class Nested {};   
      // "T:N.X.Nested"  
  
      ///   
      static explicit operator System::Int32 (X x) { return 1; }   
      // "M:N.X.op_Explicit(N.X!System.Runtime.CompilerServices.IsByValue)~System.Int32"  
   };  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)