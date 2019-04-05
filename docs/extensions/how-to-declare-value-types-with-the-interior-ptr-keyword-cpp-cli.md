---
title: 'Instrukcje: Deklarowanie typów wartości za pomocą słowa kluczowego interior_ptr (C + +/ CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: 2b75f6c4763ddd7d3fd2d802371e21c40d506b16
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026102"
---
# <a name="how-to-declare-value-types-with-the-interiorptr-keyword-ccli"></a>Instrukcje: Deklarowanie typów wartości za pomocą słowa kluczowego interior_ptr (C + +/ CLI)

**Pomocą interior_ptr** może być używany z typem wartości.

> [!IMPORTANT]
> Tej funkcji języka jest obsługiwana przez `/clr` — opcja kompilatora, ale nie za `/ZW` — opcja kompilatora.

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Następujące C + +/ interfejsu wiersza polecenia przykład pokazuje, jak używać **pomocą interior_ptr** z typem wartości.

### <a name="code"></a>Kod

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Utworzenie typu wartości **to** wskaźnika, daje w wyniku pomocą interior_ptr.

W treści niestatycznej funkcji składowej typu wartości `V`, **to** to wyrażenie typu `interior_ptr<V>` którego wartość jest adres obiektu, dla której wywołano tę funkcję.

### <a name="code"></a>Kod

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example"></a>Przykład

### <a name="description"></a>Opis

Poniższy przykład pokazuje sposób użycia operatora address-of przy użyciu statycznych elementów członkowskich.

Adres statyczny element członkowski typu Visual C++ daje wskaźnik natywny.  Adres elementu członkowskiego typu wartości statycznej jest wskaźnika zarządzanych, ponieważ składowa typu wartości jest przydzielony na stosie uruchomieniowym i mogą być przenoszone przez moduł odśmiecania pamięci.

### <a name="code"></a>Kod

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>Zobacz także

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)