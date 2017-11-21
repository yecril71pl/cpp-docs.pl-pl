---
title: Zarys zmian (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c0bbbd6b-c5c4-44cf-a6ca-c1010c377e9d
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a17ad8aca031d6345f3ded4839dbb543c1edf133
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="outline-of-changes-ccli"></a>Zarys zmian (C++/CLI)
Ten konspekt przedstawiono przykłady niektóre zmiany w języku z rozszerzeń zarządzanych dla języka C++ dla Visual C++. Kliknij link, który towarzyszy każdy element, aby uzyskać więcej informacji.  
  
## <a name="no-double-underscore-keywords"></a>Podwójne podkreślenia słów kluczowych  
 Podwójne podkreślenie przed wszystkie słowa kluczowe został usunięty, z jednym wyjątkiem. W związku z tym `__value` staje się `value`, i `__interface` staje się `interface`i tak dalej. Aby uniknąć kolizji nazw między słów kluczowych i identyfikatory w kodzie użytkownika, słowa kluczowe głównie są traktowane jako kontekstowych.  
  
 Zobacz [słowa kluczowe języka (C + +/ CLI)](../dotnet/language-keywords-cpp-cli.md) Aby uzyskać więcej informacji.  
  
## <a name="class-declarations"></a>Deklaracje klas  
 Składni zarządzanych rozszerzeń:  
  
```  
__gc class Block {};                           // reference class  
__value class Vector {};                       // value class  
__interface I {};                        // interface class  
__gc __abstract class Shape {};                // abstract class  
__gc __sealed class Shape2D : public Shape {}; // derived class  
```  
  
 Nowej składni:  
  
```  
ref class Block {};                // reference class  
value class Vector {};             // value class  
interface class I {};        // interface class  
ref class Shape abstract {};       // abstract class  
ref class Shape2D sealed: Shape{}; // derived class  
```  
  
 Zobacz [typy zarządzane (C + +/ CL)](../dotnet/managed-types-cpp-cl.md) Aby uzyskać więcej informacji.  
  
## <a name="object-declaration"></a>Deklaracja obiektu  
 Składni zarządzanych rozszerzeń:  
  
```  
public __gc class Form1 : public System::Windows::Forms::Form {  
private:  
   System::ComponentModel::Container __gc *components;  
   System::Windows::Forms::Button   __gc *button1;  
   System::Windows::Forms::DataGrid __gc *myDataGrid;     
   System::Data::DataSet  __gc *myDataSet;  
};  
```  
  
 Nowej składni:  
  
```  
public ref class Form1 : System::Windows::Forms::Form {  
   System::ComponentModel::Container^ components;  
   System::Windows::Forms::Button^ button1;  
   System::Windows::Forms::DataGrid^ myDataGrid;  
   System::Data::DataSet^ myDataSet;  
};  
```  
  
 Zobacz [deklaracja obiektu klasy odwołania CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) Aby uzyskać więcej informacji.  
  
### <a name="managed-heap-allocation"></a>Alokacja sterty zarządzanej  
 Składni zarządzanych rozszerzeń:  
  
```  
Button* button1 = new Button; // managed heap  
int *pi1 = new int;           // native heap  
Int32 *pi2 = new Int32;       // managed heap  
```  
  
 Nowej składni:  
  
```  
Button^ button1 = gcnew Button;        // managed heap  
int * pi1 = new int;                   // native heap  
Int32^ pi2 = gcnew Int32;              // managed heap  
```  
  
 Zobacz [deklaracja obiektu klasy odwołania CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) Aby uzyskać więcej informacji.  
  
### <a name="a-tracking-reference-to-no-object"></a>Odwołanie śledzące do żadnego obiektu  
 Składni zarządzanych rozszerzeń:  
  
```  
// OK: we set obj to refer to no object  
Object * obj = 0;  
  
// Error: no implicit boxing  
Object * obj2 = 1;  
```  
  
 Nowej składni:  
  
```  
// Incorrect Translation  
// causes the implicit boxing of both 0 and 1  
Object ^ obj = 0;  
Object ^ obj2 = 1;  
  
// Correct Translation  
// OK: we set obj to refer to no object  
Object ^ obj = nullptr;  
  
// OK: we initialize obj2 to an Int32^  
Object ^ obj2 = 1;  
```  
  
 Zobacz [deklaracja obiektu klasy odwołania CLR](../dotnet/declaration-of-a-clr-reference-class-object.md) Aby uzyskać więcej informacji.  
  
## <a name="array-declaration"></a>Deklaracja tablicy  
 Został zaprojektowany do tablicy CLR. Jest on podobny do stl `vector` kolekcji szablonu, ale map do odpowiadającego `System::Array` klasy — to znaczy, że nie jest implementacja szablonu.  
  
 Zobacz [deklaracja tablicy CLR](../dotnet/declaration-of-a-clr-array.md) Aby uzyskać więcej informacji.  
  
### <a name="array-as-parameter"></a>Tablica jako parametr.  
 Składnia tablicy zarządzanych rozszerzeń:  
  
```  
void PrintValues( Object* myArr __gc[]);   
void PrintValues( int myArr __gc[,,]);   
```  
  
 Nowej składni tablicy:  
  
```  
void PrintValues( array<Object^>^ myArr );  
void PrintValues( array<int,3>^ myArr );  
```  
  
### <a name="array-as-return-type"></a>Tablica jako typ zwracany  
 Składnia tablicy zarządzanych rozszerzeń:  
  
```  
Int32 f() [];   
int GetArray() __gc[];  
```  
  
 Nowej składni tablicy:  
  
```  
array<Int32>^ f();  
array<int>^ GetArray();  
```  
  
### <a name="shorthand-initialization-of-local-clr-array"></a>Skrócona inicjowania CLR lokalnej tablicy  
 Składnia tablicy zarządzanych rozszerzeń:  
  
```  
int GetArray() __gc[] {  
   int a1 __gc[] = { 1, 2, 3, 4, 5 };  
   Object* myObjArray __gc[] = { __box(26), __box(27), __box(28),  
                                 __box(29), __box(30) };  
  
   return a1;  
}  
```  
  
 Nowej składni tablicy:  
  
```  
array<int>^ GetArray() {  
   array<int>^ a1 = {1,2,3,4,5};  
   array<Object^>^ myObjArray = {26,27,28,29,30};  
  
   return a1;  
}  
```  
  
### <a name="explicit-clr-array-declaration"></a>Deklaracja tablicy CLR jawne  
 Składnia tablicy zarządzanych rozszerzeń:  
  
```  
Object* myArray[] = new Object*[2];  
String* myMat[,] = new String*[4,4];  
```  
  
 Nowej składni tablicy:  
  
```  
array<Object^>^ myArray = gcnew array<Object^>(2);  
array<String^,2>^ myMat = gcnew array<String^,2>(4,4);  
```  
  
 Nowy język: inicjowanie tablicy jawne, który następuje gcnew  
  
```  
// explicit initialization list follow gcnew   
// is not supported in Managed Extensions  
array<Object^>^ myArray =   
   gcnew array<Object^>(4){ 1, 1, 2, 3 };  
```  
  
## <a name="scalar-properties"></a>Właściwości skalarne  
 Składnia właściwości zarządzanych rozszerzeń:  
  
```  
public __gc __sealed class Vector {  
   double _x;  
  
public:  
   __property double get_x(){ return _x; }  
   __property void set_x( double newx ){ _x = newx; }  
};  
```  
  
 Nowej składni właściwości:  
  
```  
public ref class Vector sealed {   
   double _x;  
  
public:  
   property double x   
   {  
      double get()             { return _x; }  
      void   set( double newx ){ _x = newx; }  
   } // Note: no semi-colon  
};  
```  
  
 Nowy język: właściwości prostej  
  
```  
public ref class Vector sealed {   
public:  
   // equivalent shorthand property syntax  
   // backing store is not accessible  
   property double x;   
};  
```  
  
 Zobacz [deklaracja właściwości](../dotnet/property-declaration.md) Aby uzyskać więcej informacji.  
  
## <a name="indexed-properties"></a>Właściwości indeksowane  
 Rozszerzenia zarządzane indeksowane składni właściwości:  
  
```  
public __gc class Matrix {  
   float mat[,];  
  
public:   
   __property void set_Item( int r, int c, float value) { mat[r,c] = value; }  
   __property int get_Item( int r, int c ) { return mat[r,c]; }  
};  
```  
  
 Nowe właściwości indeksowanej składni:  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   property float Item [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 Nowy język: klasa poziomu właściwości indeksowanej  
  
```  
public ref class Matrix {  
   array<float, 2>^ mat;  
  
public:  
   // ok: class level indexer now  
   //     Matrix mat;  
   //     mat[ 0, 0 ] = 1;   
   //  
   // invokes the set accessor of the default indexer  
  
   property float default [int,int] {  
      float get( int r, int c ) { return mat[r,c]; }  
      void set( int r, int c, float value ) { mat[r,c] = value; }  
   }  
};  
```  
  
 Zobacz [deklaracja indeksu właściwości](../dotnet/property-index-declaration.md) Aby uzyskać więcej informacji.  
  
## <a name="overloaded-operators"></a>Operatory przeciążone  
 Składnia przeciążenia operatora zarządzanych rozszerzeń:  
  
```  
public __gc __sealed class Vector {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    op_Equality( const Vector*, const Vector* );  
   static Vector* op_Division( const Vector*, double );  
};  
  
int main() {  
   Vector *pa = new Vector( 0.231, 2.4745, 0.023 );  
   Vector *pb = new Vector( 1.475, 4.8916, -1.23 );   
  
   Vector *pc = Vector::op_Division( pa, 4.8916 );  
  
   if ( Vector::op_Equality( pa, pc ))  
      ;  
}  
```  
  
 Nowej składni przeciążenia operatora:  
  
```  
public ref class Vector sealed {  
public:  
   Vector( double x, double y, double z );  
  
   static bool    operator ==( const Vector^, const Vector^ );  
   static Vector^ operator /( const Vector^, double );  
};  
  
int main() {  
   Vector^ pa = gcnew Vector( 0.231, 2.4745, 0.023 );  
   Vector^ pb = gcnew Vector( 1.475, 4.8916, -1.23 );  
  
   Vector^ pc = pa / 4.8916;  
   if ( pc == pa )  
      ;  
}  
```  
  
 Zobacz [przeciążone operatory](../dotnet/overloaded-operators.md) Aby uzyskać więcej informacji.  
  
## <a name="conversion-operators"></a>Operatory konwersji  
 Składnia operatora konwersji zarządzanych rozszerzeń:  
  
```  
__gc struct MyDouble {  
   static MyDouble* op_Implicit( int i );   
   static int op_Explicit( MyDouble* val );  
   static String* op_Explicit( MyDouble* val );   
};  
```  
  
 Nowej składni operatora konwersji:  
  
```  
ref struct MyDouble {  
public:  
   static operator MyDouble^ ( int i );  
   static explicit operator int ( MyDouble^ val );  
   static explicit operator String^ ( MyDouble^ val );  
};  
```  
  
 Zobacz [zmiany operatorów konwersji](../dotnet/changes-to-conversion-operators.md) Aby uzyskać więcej informacji.  
  
## <a name="explicit-override-of-an-interface-member"></a>Jawne przesłanianie elementu członkowskiego interfejsu  
 Rozszerzenia zarządzane jawne zastąpienie składni:  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 Składnia jawnego przesłaniania nowe:  
  
```  
public ref class R : public ICloneable {  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R   
   virtual R^ Clone();  
};  
```  
  
 Zobacz [jawne zastąpienie elementu członkowskiego interfejsu](../dotnet/explicit-override-of-an-interface-member.md) Aby uzyskać więcej informacji.  
  
## <a name="private-virtual-functions"></a>Prywatne funkcje wirtualne  
 Składnia prywatnej funkcji wirtualnej zarządzanych rozszerzeń:  
  
```  
__gc class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
__gc class Derived : public Base {  
public:  
   // ok: g() overrides Base::g()  
   virtual void g();  
};  
```  
  
 Nowej składni prywatnej funkcji wirtualnej  
  
```  
ref class Base {  
private:  
   // inaccessible to a derived class  
   virtual void g();   
};  
  
ref class Derived : public Base {  
public:  
   // error: cannot override: Base::g() is inaccessible  
   virtual void g() override;  
};  
```  
  
 Zobacz [prywatne funkcje wirtualne](../dotnet/private-virtual-functions.md) Aby uzyskać więcej informacji.  
  
## <a name="clr-enum-type"></a>Typ wyliczenia CLR  
 Składnia wyliczenia zarządzanych rozszerzeń:  
  
```  
__value enum e1 { fail, pass };  
public __value enum e2 : unsigned short  {   
   not_ok = 1024,   
   maybe, ok = 2048   
};    
```  
  
 Nowej składni wyliczenia:  
  
```  
enum class e1 { fail, pass };  
public enum class e2 : unsigned short {   
   not_ok = 1024,  
   maybe, ok = 2048   
};  
```  
  
 Oprócz małych zmiany składni zmieniono zachowanie typ wyliczenia CLR na kilka sposobów:  
  
-   Deklaracja przekazująca dalej wyliczenie CLR nie jest już obsługiwana.  
  
-   Rozpoznawanie przeciążenia między wbudowanych typów arytmetycznych i hierarchia klas obiektów została wycofana między rozszerzeń zarządzanych i program Visual C++. Jako efekt uboczny wyliczenia CLR są już niejawnie konwertowane typów arytmetycznych.  
  
-   W nowej składni wyliczenia CLR zachowuje własną zakresu, który nie jest w przypadku rozszerzeń zarządzanych. Wcześniej moduły wyliczające były widoczne w zakresie zawierającym wyliczenia; teraz moduły wyliczające znajdują się w zakresie wyliczenia.  
  
 Zobacz [typ wyliczenia CLR](../dotnet/clr-enum-type.md) Aby uzyskać więcej informacji.  
  
## <a name="removal-of-box-keyword"></a>Usunięcie __box — słowo kluczowe  
 Konwersja boxing składni zarządzanych rozszerzeń:  
  
```  
Object *o = __box( 1024 ); // explicit boxing  
```  
  
 Nowej składni opakowanie:  
  
```  
Object ^o = 1024; // implicit boxing  
```  
  
 Zobacz [A Śledzenie dojścia do wartości opakowany](../dotnet/a-tracking-handle-to-a-boxed-value.md) Aby uzyskać więcej informacji.  
  
## <a name="pinning-pointer"></a>Unieruchamianie wskaźników  
 Rozszerzenia zarządzane przypinanie wskaźnika składni:  
  
```  
__gc struct H { int j; };  
  
int main() {  
   H * h = new H;  
   int __pin * k = & h -> j;  
};  
```  
  
 Nowej składni wskaźnika przypinania:  
  
```  
ref struct H { int j; };  
  
int main() {  
   H^ h = gcnew H;  
   pin_ptr<int> k = &h->j;  
}  
```  
  
 Zobacz [semantyka typów wartości](../dotnet/value-type-semantics.md) Aby uzyskać więcej informacji.  
  
## <a name="typeof-keyword-becomes-typeid"></a>__typeof — słowo kluczowe staje się typeid  
 Składnia typeof zarządzanych rozszerzeń:  
  
```  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 Nowej składni typeid:  
  
```  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
 Zobacz [typeof operatorem T::TypeID](../dotnet/typeof-goes-to-t-typeid.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [C + +/ CLI Elementarz migracji](../dotnet/cpp-cli-migration-primer.md)   
 [Component Extensions dla platform środowiska uruchomieniowego](../windows/component-extensions-for-runtime-platforms.md)


