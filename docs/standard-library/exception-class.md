---
title: Klasa Exception | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec1cfe2be7f6a2172b6624f15cb3dcde4f0ba3c2
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957021"
---
# <a name="exception-class"></a>Klasa exception

Klasa służy jako klasa bazowa dla wszystkich wyjątków generowanych przez niektóre wyrażenia i standardowej biblioteki języka C++.

## <a name="syntax"></a>Składnia

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
   };
```

## <a name="remarks"></a>Uwagi

W szczególności, ta klasa bazowa jest katalogiem głównym klas standardowych wyjątków zdefiniowanych w [ \<stdexcept >](../standard-library/stdexcept.md). Wartość zwrócona przez obiekt string, C `what` jest określony przez konstruktora domyślnego, ale mogą być określone przez konstruktory dla niektórych klas pochodnych w postaci ciągu zdefiniowane w implementacji C. Żadna z funkcji elementu członkowskiego generuje żadnych wyjątków.

**Int** parametr umożliwia określenie, że pamięć nie powinna zostać przydzielona. Wartość **int** jest ignorowana.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` i `exception(const char* const &message, int)` są rozszerzenia Microsoft do standardowej biblioteki języka C++.

## <a name="example"></a>Przykład

Przykłady użycia, które dziedziczą z klasy wyjątku standardowa `exception` , zobacz jedną z klas zdefiniowanych w [ \<stdexcept >](../standard-library/stdexcept.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyjątku >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
