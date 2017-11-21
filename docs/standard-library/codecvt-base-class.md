---
title: "codecvt_base — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocale/std::codecvt_base
dev_langs: C++
helpviewer_keywords: codecvt_base class
ms.assetid: 7e95c083-91b4-4b3f-8918-0d4ea244a040
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5ead26920f0b1aa7f49c43b60640a03241138163
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="codecvtbase-class"></a>codecvt_base — Klasa
Klasa podstawowa dla codecvt — klasa, która służy do definiowania typu wyliczeniowego, określany jako **wynik**, używana jako typ zwracany dla funkcji Członkowskich aspektu wyniku konwersji.  
  
## <a name="syntax"></a>Składnia  
  
```
class codecvt_base : public locale::facet {
public:
    enum result {ok, partial, error, noconv};
    codecvt_base( size_t _Refs = 0);
    bool always_noconv() const;
    int max_length() const;
    int encoding() const;
    ~codecvt_base()

protected:
    virtual bool do_always_noconv() const;
    virtual int do_max_length() const;
    virtual int do_encoding() const;
};
```  
  
## <a name="remarks"></a>Uwagi  
 Klasa opisuje wyliczenia, które są wspólne dla wszystkich specjalizacji szablonu klasy [codecvt](../standard-library/codecvt-class.md). Wynik wyliczenie opisano możliwe wartości zwracane z [do_in](../standard-library/codecvt-class.md#do_in) lub [do_out](../standard-library/codecvt-class.md#do_out):  
  
- **OK** Jeśli konwersja między kodowanie znaków wewnętrznych i zewnętrznych zakończy się powodzeniem.  
  
- **częściowe** Jeśli element docelowy nie jest wystarczająco duży dla konwersja powiodła się.  
  
- **Błąd** Jeśli sekwencji źródłowej jest dotknięty sformułowany.  
  
- **noconv** , gdy funkcja wykonuje brak konwersji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<ustawień regionalnych >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



