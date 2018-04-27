---
title: wyjątek klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- exception
dev_langs:
- C++
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 713600a72886b713c58c4a449c6f5270a3ccfe9a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="exception-class"></a>Klasa exception

Klasa służy jako klasa podstawowa dla wszystkich wyjątków zgłoszonych przez niektórych wyrażeń i standardowa biblioteka C++.

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

W szczególności ta klasa podstawowa jest katalogiem głównym standardowe wyjątek klas zdefiniowanych w [ \<stdexcept — >](../standard-library/stdexcept.md). Wartość zwrócona przez ciąg C `what` jest określony przez konstruktora domyślnego, ale może być zdefiniowana przez konstruktorów niektórych klas pochodnych jako ciąg C zdefiniowane w implementacji. Brak funkcji Członkowskich generują żadnych wyjątków.

`int` Parametr umożliwia określenie, czy można przydzielić pamięci. Wartość `int` jest ignorowana.

> [!NOTE]
> Konstruktory `exception(const char* const &message)` i `exception(const char* const &message, int)` są rozszerzenia Microsoft do standardowej biblioteki C++.

## <a name="example"></a>Przykład

Przykłady użycia klasy standardowe wyjątków, które dziedziczą z `exception` , zobacz jedną z klas zdefiniowanych w [ \<stdexcept — >](../standard-library/stdexcept.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wyjątku >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
