---
title: '&lt;SeeAlso — > (komentarze dokumentacji C++)'
ms.date: 11/04/2016
f1_keywords:
- <seealso>
- seealso
helpviewer_keywords:
- seealso C++ XML tag
- <seealso> C++ XML tag
ms.assetid: cb33d100-9c50-4485-8d0c-573429eff155
ms.openlocfilehash: ea399e98723a265ef3c17f2282b7c81299b4abc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318839"
---
# <a name="ltseealsogt"></a>&lt;seealso&gt;

\<SeeAlso — > należy określić tekst, który możesz chcieć pojawiają się w sekcji Zobacz też. Użyj [ \<zobacz >](see-visual-cpp.md) określić łącze między w tekście.

## <a name="syntax"></a>Składnia

```
<seealso cref="member"/>
```

#### <a name="parameters"></a>Parametry

*Element członkowski*<br/>
Odwołanie do elementu członkowskiego lub pola, które są dostępne do wywoływania z bieżącym środowisku kompilacji.  Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.

Kompilator sprawdza, czy dany element kodu istnieje i jest rozpoznawana jako `member` do nazwy elementu w danych wyjściowych XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](see-visual-cpp.md).

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

Zobacz [ \<podsumowania >](summary-visual-cpp.md) na przykład za pomocą \<SeeAlso — >.

Za pomocą kompilatora MSVC będzie próbował rozpoznać odwołania cref w jednym przebiegu za pomocą komentarzy dokumentacji.  W związku z tym, jeśli przy użyciu reguł wyszukiwania C++, symbolu nie można odnaleźć kompilatora odwołania zostaną oznaczone jako nierozwiązane.

## <a name="example"></a>Przykład

W poniższym przykładzie nierozpoznanych symboli jest przywoływany w cref. Komentarz XML dla cref do B::Test będzie `<seealso cref="!:B::Test" />`, odwołanie do A::Test jest poprawnie sformułowanym `<seealso cref="M:A.Test" />`.

```
// xml_seealso_tag.cpp
// compile with: /LD /clr /doc
// post-build command: xdcmake xml_seealso_tag.dll

/// Text for class A.
public ref struct A {
   /// <summary><seealso cref="A::Test"/>
   /// <seealso cref="B::Test"/>
   /// </summary>
   void MyMethod(int Int1) {}

   /// text
   void Test() {}
};

/// Text for class B.
public ref struct B {
   void Test() {}
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
