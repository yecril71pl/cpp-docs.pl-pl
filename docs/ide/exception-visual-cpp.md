---
title: '&lt;wyjątek&gt; (Visual C++) | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- exception
- <exception>
dev_langs:
- C++
helpviewer_keywords:
- <exception> C++ XML tag
- exception C++ XML tag
ms.assetid: 24451e79-9b89-4b77-98fb-702c6516b818
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bb7b5f4e153ca892cf10f8c5cbe6fe1bebbd20f2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419973"
---
# <a name="ltexceptiongt-visual-c"></a>&lt;wyjątek&gt; (Visual C++)

\<Wyjątku > należy określić, które wyjątki mogą zostać wygenerowane. Ten tag jest stosowany do definicji metody.

## <a name="syntax"></a>Składnia

```
<exception cref="member">description</exception>
```

#### <a name="parameters"></a>Parametry

*Element członkowski*<br/>
Odwołanie do wyjątek, który jest dostępny w bieżącym środowisku kompilacji. Przy użyciu reguł wyszukiwania nazwy, kompilator sprawdza, czy dany wyjątek istnieje i tłumaczy `member` nazwę kanoniczną element w danych wyjściowych XML.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `member`.

Nazwę należy ująć w pojedyncze lub podwójne znaki cudzysłowu.

Aby uzyskać informacje na temat tworzenia cref odwołanie do typu ogólnego, zobacz [ \<zobacz >](../ide/see-visual-cpp.md).

*Opis elementu*<br/>
Opis.

## <a name="remarks"></a>Uwagi

Kompiluj przy użyciu [/doc](../build/reference/doc-process-documentation-comments-c-cpp.md) do Przetwarzaj komentarze dokumentacji do pliku.

Kompilator języka Visual C++ będzie próbował rozpoznać odwołania cref w jednym przebiegu za pomocą komentarzy dokumentacji.  W związku z tym, jeśli przy użyciu reguł wyszukiwania C++, symbolu nie można odnaleźć kompilatora odwołania zostaną oznaczone jako nierozwiązane. Zobacz [ \<SeeAlso — >](../ide/seealso-visual-cpp.md) Aby uzyskać więcej informacji.

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

## <a name="see-also"></a>Zobacz też

[Dokumentacja XML](../ide/xml-documentation-visual-cpp.md)