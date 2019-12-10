---
title: '&lt;paramref > (C++ Komentarze do dokumentacji)'
ms.date: 11/04/2016
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- paramref C++ XML tag
- <paramref> C++ XML tag
ms.assetid: c5730dc2-7159-421f-b2d5-bb971e307122
ms.openlocfilehash: 1f4e9cb0e6b39e4da78e78048342dac2ecc9deea
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988690"
---
# <a name="ltparamrefgt"></a>&lt;paramref&gt;

Tag \<paramref > umożliwia wskazanie, że słowo jest parametrem. Plik. XML można przetworzyć, aby sformatować ten parametr w dowolny sposób.

## <a name="syntax"></a>Składnia

```
<paramref name="name"/>
```

#### <a name="parameters"></a>Parametry

*Nazwa*<br/>
Nazwa parametru, do którego się odwołuje.  Ujmij nazwę w pojedyncze lub podwójne cudzysłowy.  Kompilator generuje ostrzeżenie, jeśli nie znajdzie `name`.

## <a name="remarks"></a>Uwagi

Kompiluj z [/doc](doc-process-documentation-comments-c-cpp.md) , aby przetwarzać komentarze dokumentacji do pliku.

## <a name="example"></a>Przykład

```cpp
// xml_paramref_tag.cpp
// compile with: /clr /doc /LD
// post-build command: xdcmake xml_paramref_tag.dll
/// Text for class MyClass.
public ref class MyClass {
   /// <summary>MyMethod is a method in the MyClass class.
   /// The <paramref name="Int1"/> parameter takes a number.
   /// </summary>
   void MyMethod(int Int1) {}
};
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja XML](xml-documentation-visual-cpp.md)
