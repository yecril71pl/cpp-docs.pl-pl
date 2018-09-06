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
ms.openlocfilehash: ce44cd7c8d6112859990feb4067e9160f284548b
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894825"
---
# <a name="xml-file-processing"></a>Przetwarzanie pliku .Xml

Kompilator generuje ciąg Identyfikatora dla każdego konstrukcji w kodzie, który jest oznaczony do generowania dokumentacji. Aby uzyskać więcej informacji, zobacz [zalecane tagi komentarzy dokumentacji](../ide/recommended-tags-for-documentation-comments-visual-cpp.md). Ciąg Identyfikatora jednoznacznie identyfikuje konstrukcja. Programów przetwarzających pliku XML, który umożliwia Zidentyfikuj odpowiednie środowiska .NET Framework metadane lub odbicie element dotyczy dokumentacji ciąg Identyfikatora.

Pliku XML, który nie jest hierarchiczną reprezentację kodu, jest płaska lista identyfikatorem wygenerowany dla każdego elementu.

Kompilator stosuje następujące reguły podczas generowania ciągi identyfikatorów:

- Biały znak nie zostanie umieszczony w ciągu.

- Pierwsza część ciąg Identyfikatora określa rodzaj elementu członkowskiego są identyfikowane za pomocą pojedynczy znak z dwukropkiem. Używane są następujące typy elementu członkowskiego:

   |Znak|Opis|
   |---------------|-----------------|
   |N|— przestrzeń nazw<br /><br /> Nie można dodać komentarze dokumentacji do przestrzeni nazw, możliwe są cref odwołania do przestrzeni nazw.|
   |T|Typ: klasy, interfejsu, struktury, wyliczenia, delegat|
   |D|— klasa typedef|
   |F|pole|
   |P|właściwości (w tym indeksatory lub innych właściwości indeksowane)|
   |M|metody (w tym specjalnych metodami, takimi jak konstruktory, operatorów i tak dalej)|
   |E|zdarzenie|
   |!|Ciąg błędu<br /><br /> Pozostała część ciągu zawiera informacje o tym błędzie. Kompilator języka Visual C++ generuje informacje o błędzie dla łączy, których nie można rozpoznać.|

- Druga część ciągu jest w pełni kwalifikowana nazwa elementu, począwszy od głównego obszaru nazw. Nazwa elementu, jego otaczającego typu lub typów i przestrzeni nazw są oddzielone kropkami. Jeśli nazwa elementu zawiera kropek, są one zastąpione przez znak kratki (#). Zakłada się, że żaden element ma znak kratki bezpośrednio w jego nazwę. Na przykład w pełni kwalifikowanej nazwy `String` Konstruktor może być "System.String.#ctor".

- Dla właściwości i metod w przypadku argumentów dla metody, na liście argumentów w nawiasach jest zgodna. Jeśli nie ma żadnych argumentów, nawiasy nie są obecne. Argumenty są oddzielone przecinkami. Kodowanie każdego argumentu następuje bezpośrednio, jak jest zakodowany w podpisie .NET Framework:

   - Typy podstawowe. Regularne typów (ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE) są reprezentowane jako w pełni kwalifikowaną nazwę typu.

   - Typy wewnętrzne (na przykład ELEMENT_TYPE_I4 ELEMENT_TYPE_OBJECT, ELEMENT_TYPE_STRING, ELEMENT_TYPE_TYPEDBYREF. i ELEMENT_TYPE_VOID) są reprezentowane jako w pełni kwalifikowaną nazwę odpowiedniego typu pełną, na przykład **System.Int32** lub **System.TypedReference**.

   - ELEMENT_TYPE_PTR jest reprezentowany jako "*" zgodnie z zmodyfikowany typ.

   - Pole jest reprezentowany jako "\@" po modyfikacji typu.

   - ELEMENT_TYPE_PINNED jest reprezentowany jako "^" po modyfikacji typu. Kompilator języka Visual C++ generuje nigdy nie tak.

   - ELEMENT_TYPE_CMOD_REQ jest reprezentowany jako "&#124;" i w pełni kwalifikowaną nazwę klasy modyfikator, zmodyfikowany typ następujące. Kompilator języka Visual C++ generuje nigdy nie tak.

   - ELEMENT_TYPE_CMOD_OPT jest reprezentowany jako "!" i w pełni kwalifikowaną nazwę klasy modyfikator, zmodyfikowany typ następujące.

   - ELEMENT_TYPE_SZARRAY jest reprezentowany jako "[]", zgodnie z typem elementu tablicy.

   - ELEMENT_TYPE_GENERICARRAY jest reprezentowany jako "[?]" po typ elementu tablicy. Kompilator języka Visual C++ generuje nigdy nie tak.

   - ELEMENT_TYPE_ARRAY jest reprezentowany jako [*ich*:`size`,*ich*:`size`] gdzie liczba przecinków jest ranga - 1 i dolne granice i rozmiaru każdego wymiaru, jeśli znane są reprezentowane w zapisie dziesiętnym. Jeśli dolna granica lub rozmiar nie zostanie określony, po prostu zostanie pominięta. W przypadku pominięcia dolną granicę i rozmiar dla określonego wymiaru ":" pominięto w także. Na przykład, to 2-wymiarowej tablicy przy użyciu 1 jako nieokreślony rozmiary i dolne granice [1:, 1:].

   - ELEMENT_TYPE_FNPTR jest reprezentowany jako "= FUNC:`type`(*podpisu*)", gdzie `type` jest zwracany typ i *podpisu* jest argumenty metody. Jeśli nie ma żadnych argumentów, nawiasy są pomijane. Kompilator języka Visual C++ generuje nigdy nie tak.

   Następujące składniki podpis nie są reprezentowane, ponieważ nigdy nie są one używane do różnicujący przeciążonych metod:

   - Konwencja wywoływania

   - Zwracany typ

   - ELEMENT ELEMENT_TYPE_SENTINEL

- Tylko operatory konwersji, aby uzyskać wartość zwracaną metody jest zakodowane jako "~" następuje zwracany typ, jak wcześniej zakodowany.

- Dla typów ogólnych Nazwa typu zostanie uzupełniona o znaczników Wstecz, a następnie na liczbę wskazującą liczbę parametrów typu genetycznego.  Na przykład

    ```  
    <member name="T:MyClass`2">
    ```  

   Dla typu, który jest zdefiniowany jako `public class MyClass<T, U>`.

   Dla metod biorąc typów podstawowych jako parametrów, parametry typu ogólnego są określane jako numery poprzedzone znakiem wstecz znaczniki (na przykład \`0, \`1).  Liczba, każda reprezentująca notacji tablicę indeksowaną od zera dla ogólnych parametrów typu.

## <a name="example"></a>Przykład

W poniższych przykładach pokazano, jak identyfikator ciągi dla klasy i jej elementów członkowskich zostanie wygenerowany.

```cpp
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