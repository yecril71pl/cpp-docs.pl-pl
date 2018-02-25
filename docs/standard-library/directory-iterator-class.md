---
title: "directory_iterator — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.workload:
- cplusplus
ms.openlocfilehash: 27152fc2ebc7944e4b96dce75937ac3c3b04616d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="directoryiterator-class"></a>directory_iterator — klasa
W tym artykule opisano iterację wejściowych, które sekwencji za pomocą nazwy plików w katalogu. Dla iteratora X, wyrażenie * X ocenia się do obiektu directory_entry — klasa, która opakowuje nazwę pliku i wszystkie znane o jej stanie.  
  
 Klasa przechowuje obiekt typu ścieżki, nazywany mydir tutaj na potrzeby specyfikacji, który reprezentuje nazwę katalogu, który ma być sekwencjonowania, a obiekt directory_entry — typ o nazwie w tym miejscu myentry, która reprezentuje bieżący nazwę pliku w katalogu Sekwencja. Obiekt domyślne skonstruowany directory_entry — typ ma pathname mydir pusty i reprezentuje iteratora sekwencja kończenia.  
  
 Na przykład, dla danego katalogu abc z wpisów def i ghi, kod:  
  
 `for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`  
  
 Wywołanie odwiedzi path("abc/def") argumentów i path("abc/ghi").  
  
 Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [nawigacji systemu plików (C++)](../standard-library/file-system-navigation.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
class directory_iterator;  
```  
  
## <a name="directoryiteratordirectoryiterator"></a>directory_iterator::directory_iterator  
  
```  
directory_iterator() noexcept;  
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;  
directory_iterator(const directory_iterator&) = default;  
directory_iterator(directory_iterator&&) noexcept = default;  
```  
  
 Pierwszy konstruktora tworzy iteratora sekwencja kończenia. Konstruktory drugiego i trzeciego przechowywania pval w mydir, a następnie spróbuj otwierać i odczytywać mydir jako katalog. W przypadku powodzenia przechowują pierwszej nazwy pliku w katalogu w myentry; w przeciwnym razie wygenerowanie iteratora sekwencja kończenia.  
  
 Domyślne construtors działają zgodnie z oczekiwaniami.  
  
## <a name="directoryiteratorincrement"></a>directory_iterator::Increment  
  
```  
directory_iterator& increment(error_code& ec) noexcept;  
```  
  
 Funkcja próbuje przejść do następnej nazwy pliku w katalogu. W przypadku powodzenia przechowuje nazwę tego pliku w myentry; w przeciwnym razie tworzy iteratora sekwencja kończenia.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator! =  
  
```  
bool operator!=(const directory_iterator& right) const;
```  
  
 Zwraca element członkowski operatora! (* to == prawej strony).  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator=  
  
```  
directory_iterator& operator=(const directory_iterator&) = default;  
directory_iterator& operator=(directory_iterator&&) noexcept = default;  
```  
  
 Operatory przypisania domyślnego elementu członkowskiego działają zgodnie z oczekiwaniami.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator==  
  
```  
bool operator==(const directory_iterator& right) const;
```  
  
 Operator członkowski zwraca wartość true tylko wtedy, gdy oba * to oraz prawo Iteratory sekwencja kończenia lub obie są nie end elementu sekwencji — Iteratory.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator *  
  
```  
const directory_entry& operator*() const;
```  
  
 Operator członkowski zwraca myentry.  
  
## <a name="directoryiteratoroperator-"></a>directory_iterator::operator ->  
  
```  
const directory_entry * operator->() const;
```  
  
 Funkcja członkowska zwraca & ** to.  
  
## <a name="directoryiteratoroperator"></a>directory_iterator::operator ++  
  
```  
directory_iterator& operator++();
directory_iterator& operator++(int);
```  
  
 Pierwszy funkcji członkowskiej wywołuje increment(), a następnie zwraca * to. Drugi funkcji członkowskiej tworzy kopię obiektu, wywołuje increment(), a następnie zwraca kopii.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<eksperymentalne/filesystem >  
  
 **Namespace:** std::experimental::filesystem  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [\<filesystem>](../standard-library/filesystem.md)   
 [Nawigacja w systemie plików (C++)](../standard-library/file-system-navigation.md)

