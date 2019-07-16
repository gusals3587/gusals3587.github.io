---
layout: default
permalink: /week3/crack
---

# tldr
아래와 같이 비밀번호를 해독하는 프로그램을 작성하시오

	./crack 50fkUxYHbnXGw
	rofl

# Background

요즘에 리눅스가 돌아가고 있는 컴퓨터에는 `/etc/shadow`라는 파일이 있습니다. 이 파일 안에는 컴퓨터 사용자들의 이름과 비밀번호가 들어 있죠. 다행히, 비밀번호들은 '그 자체'로 저장되어 있지 않고, "해쉬 함수"라는 것을 통해 '해쉬'라고 변하고, 그 해쉬가 저장되어 있습니다. 컴퓨터 사용자가 이름과 비밀번호를 통해 로그인을 하면, 비밀번호는 동일한 "해쉬 함수"의 결과물을 `/etc/shadow` 안에 있는 문자열과 비교하면서, 두 개의 해쉬가 동일하다면, 유저는 접속 권한을 얻게 됩니다. 당신이 옛날에 무슨 비밀번호를 까먹었을 때, 비밀번호를 찾을 수는 없지만, 비밀번호를 변경할 수는 있다는 것을 들었을 것 입니다. 이러한 이유는 그 웹사이트 회사가 볼 수 있는 건 당신의 비밀번호의 '해쉬' 밖에 못 보지만, 새로운 해쉬를 만들고, 본래 비밀번호와 해쉬를 바꿀 수는 있기 때문입니다.

`/etc/shadow`안에 있는 비밀번호는 해쉬로 변환되어 있지만, 해쉬 함수는 보안상 안전하지 않을 상황이 있습니다. 실제로 해커들이 `/etc/shadow`같은 파일을 어떻게든 얻으면, 모든 비밀번호의 해쉬를 시도해보면서, 실제 비밀번호를 알아낼 수도 있습니다. 아래는 '이름:비밀번호' 모양으로 정렬된 예제의 `/etc/shadow` 파일입니다. 물론 실제 파일은 다를 수도 있습니다.

	anushree:50xcIMJ0y.RXo
	brian:50mjprEcqC/ts
	bjbrown:50GApilQSG3E2
	lloyd:50n0AAUD.pL8g
	malan:50CcfIk1QrPr6
	maria:509nVI8B9VfuA
	natmelo:50JIIyhDORqMU
	rob:50JGnXUgaafgc
	stelios:51u8F0dkeDSbY
	zamyla:50cI2vYkF0YU2
	
# Specification
비밀번호를 해독하는 `crack`라는 프로그램을 디자인하고 작성하세요


+ 당신의 프로그램은 비밀번호의 해쉬를 argument로 받아야 합니다
+ 당신의 프로그램이 아무 argument도 받지 않았다면, 에러를 출력하고 `main`이 `1`을 리턴하면서 프로그램이 끝나야 합니다. (나중에 프로그램 추가)
+ 해쉬를 받았다면, 당신의 프로그램은 해쉬의 해독을 시도하고, 원래 비밀번호를 출력해야 합니다. 이 작업이 모두 다 끝나면, `main`은 `0`을 리턴하고, 프로그램이 끝나야 합니다.
+ 받은 모든 해쉬의 비밀번호는 C의 DES 기반 crypt 해쉬 함수를 이용한다는 가정을 합니다.
+ 모든 비밀번호는 5글자 이하(세상에나!!) 라는 가정을 합니다.
+ 모든 비밀번호는 전부 다 영문 알파벳으로 구성돼어있다는 가정을 합니다. (소문자, 대문자 상관 없이)

# Walkthrough
**이 비디오는 (번역하지 않았지만) 비밀번호가 4글자 이하라고 합니다. 프로그램을 작성할 때는 5글자 이하라는 가정을 해야 합니다**

<div class="iframe-container">
<iframe allowfullscreen="" frameborder="0" src="https://www.youtube.com/embed/w78QYcmpA8o?rel=0"></iframe>
</div>

# Usage

당신의 프로그램은 아래에 있는 예시처럼 행동해야 합니다. 밑줄 친 텍스트는 어떤 유저가 터미널에 입력한 값이라는 가정을 합니다.

<pre class="pygments highlight"><code>$ <span class="underline">./crack</span>
Usage: ./crack hash</code></pre>

<pre class="pygments highlight"><code>$ <span class="underline">./crack 50JGnXUgaafgc</span>
rofl</code></pre>
	
# Testing
이번에는 `check50`는 없지만, `Background` 안에 있던 비밀번호 10개를 모두 다 해독할 수 있다면 통과 입니다!

# Hints


+ `crypt`에 대해 읽어 보십시오! 특히 'salt'에 관한 설명을 자세히 읽으세요!

      man crypt
	
	
이 man (manual의 줄일말) 페이지에 의하면, 당신의 프로그램 위에는 `crypt`을 이용하기 위해서는

	#define _XOPEN_SOURCE
	#include <unistd.h>
	
가 있어야 할 것 같네요..


+ 당신의 프로그램의 효율을 확인할 때, 당신의 프로그램이 비밀번호를 해독하는데 걸리는 시간을 확인하고 싶으면,  
unix의 time 프로그램을 이용하면 됩니다.

      time ./crack 50JGnXUgaafgc
	  
[back](../)
