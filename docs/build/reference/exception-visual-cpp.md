---
title: '&lt;wyjątek > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
ms.openlocfilehash: 327c1bc27f4ae71aa214e09f375f963dad5b33d7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823297"
---
# <a name="ltexceptiongt"></a>&lt;wyjątek&gt;

\<Wyjątku > należy określić, które wyjątki mogą zostać wygenerowane. Ten tag jest stosowany do definicji metody.

## <a name="syntax"></a>Składnia

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parametry

*Element członkowski*<br/>
Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji. Przy użyciu reguł wyszukiwania nazwy, kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` nazwę kanoniczną element w danych wyjściowych XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.

Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](see-visual-cpp.md).

*description*<br/>
Opis.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

Za pomocą kompilatora MSVC będzie próbował rozpoznać odwołania cref w jednym przebiegu za pomocą komentarzy dokumentacji.  W związku z tym, jeśli przy użyciu reguł wyszukiwania C++, symbolu nie można odnaleźć kompilatora odwołania zostaną oznaczone jako nierozwiązane. Zobacz [ \<SeeAlso — >](seealso-visual-cpp.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

```
// xml_exception_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_exception_tag.dll
using namespace System;

/// Text for class EClass.
public ref class EClass : public Exception {
   // class definition ...
};

/// <exception cref="System.Exception">Thrown when... .</exception>
public ref class TestClass {
   void Test() {
      try {
      }
      catch(EClass^) {
      }
   }
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
