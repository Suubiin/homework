### 구현 결과
![apple과제 (1)](https://github.com/Suubiin/homework/assets/127467411/e3aaac7c-6178-4876-90b2-628fda84e322)

### 마크업
  <!-- ipad-pro -->
    <div class="card ipad-pro">
      <h1>iPad Pro</h1>
      <h2>
        놀라우리만치 얇다.
        <span class="line-break"><br></span>
        엄청나게 강력하다.
      </h2>
      <p>출시일 추후 공개</p>
      <ul>
        <li class="more-data"><a href="/">더 알아보기</a></li>
        <li class="price"><a href="/">가격 보기</a></li>
      </ul>
    </div>

카드 각각을 위와 같은 구조로 마크업하였고, 7개의 카드를 .container 라는 클래스명을 가진 div로 감쌌다.

### 스타일링
## 배경 이미지

  .ipad-pro{
    background-image: image-set(url(./../products/ipad_pro.jpeg) 1x, 
                                url(./../products/ipad_pro_2x.jpeg) 2x);
  }
  @media (min-width: 1024px){
    .ipad-pro{
      background-image: image-set(url(./../products/ipad_pro_wide.jpeg) 1x, 
                                  url(./../products/ipad_pro_wide_2x.jpeg) 2x);
    }
  }

기본적으로 small screen 이미지를 이미지셋으로 지정하였고, 미디어쿼리를 사용하여 large screen 이미지를 이미지셋으로 지정하였다.

## 배경 속성 설정 및 태그 배치
  .card{
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    height: var(--size);
    display: grid;
    grid-template-columns: 1fr;
    grid-auto-rows: max-content;
    justify-items: center;
    gap: var(--small-spacing);
  }
배경 속성을 위와 같이 지정하였다.
<div> 안의 요소들을 grid를 이용하여 배치하였고 요소 간 gap을 지정하였다.

## h1
  h1{
    font-size: var(--large-text);
    margin-top: var(--large-spacing);
    font-weight: bold;
    
    @media (min-width: 1024px){
      font-size: var(--extra-large-text);
      margin-top: var(--extra-large-spacing);
    }
  }
small screen일 때와 large screen일 때의 글자 크기, 위쪽 여백을 위와 같이 지정하였다.

## h2
  h2 {
    font-size: var(--base-text);
    line-height: var(--line-normal);
    text-align: center;
    
    @media (min-width: 1024px) {
      font-size: var(--medium-text);
      
      .line-break{
        display: none;
      }
    }
  }
마크업할 때 small screen 기준으로 줄바꿈이 되는 곳에 
  <span class="line-break"><br></span> 
을 추가하였다. 그리고 large screen이 될 때 display: none;을 하여 줄바꿈이 되지 않도록 하였다.

## h1, h2의 글자색
  .card:nth-child(even) h1, .card:nth-child(even) h2{
    color: var(--black);
  }

  .card:nth-child(odd) h1, .card:nth-child(odd) h2{
    color: var(--white);
  }
홀수번째 카드는 배경이 검정색, h1, h2의 글자색이 흰색이고 짝수번째 카드는 그 반대였기 때문에 nth-child를 이용하여 글자색을 지정하였다.

## p
  p{
    font-size: var(--small-text);
    color: var(--gray);
  }

## 링크 버튼
  ul{
    display: flex;
    flex-flow: row nowrap;
    color: var(--white);
    font-size: var(--xx-small-text);

    @media (min-width: 1024px){
      font-size: var(--x-small-text);
    }
  }

  li{
    border-radius: 50px;
    padding: var(--x-small-spacing) var(--small-spacing);
  }

flex를 사용하여 가로로 버튼을 배치하였고, border-radius와 padding 값을 지정하였다.

# '더 알아보기' 링크 버튼
  .more-data{
    border: 1px solid var(--blue-400);
    background-color: var(--blue-400);
    
    &:hover{
      background-color: var(--blue-200);
      border-color: var(--blue-200);
    }
  }

  .card:nth-child(even) .more-data {
    background-color: var(--black);
    border-color: var(--black);
  }
리스트 태그에 .more-data라는 클래스를 지정하였다. 기본 배경과 테두리 색상을 --blue-400으로 지정하였고 마우스를 올렸을 경우 --blue-200으로 바뀌도록 하였다.
그리고 짝수번째 카드는 nth-child를 사용하여 배경과 테두리 색상을 --black으로 설정하였다.

# '가격 보기' 링크 버튼
  .price{
    color: var(--blue-400);
    border: 1px solid var(--blue-400);
    margin-left: var(--base-spacing);

    &:hover{
      background-color: var(--blue-200);
      border-color: var(--blue-200);
      color: var(--white);
    }
  }

  .card:nth-child(even) .price {
    border-color: var(--black);
    color: var(--black);

    &:hover{
      background-color: var(--black);
      color: var(--white)
    }
  }
'더 알아보기' 버튼과 마찬가지로 리스트 태그에 .price라는 클래스를 지정하였고 짝수번째 카드일 때와 홀수번째 카드일 때의 색상을 다르게 지정하였다.
그리고 '더 알아보기' 버튼과 '가격 보기' 버튼 사이에 margin 값을 margin-left를 이용하여 지정하였다.

## 레이아웃
  .container{
    display: grid;
    grid-template-columns: 1fr;
    grid-template-rows: repeat(7, 1fr);
    gap: var(--base-spacing);

    @media (min-width: 1024px){
      grid-template-columns: 1fr 1fr;
      grid-template-rows: repeat(5, 1fr);

      .ipad-pro{
        grid-area: 1/1/2/3;
      }
    
      .ipad-air{
        grid-area: 2/1/3/3;
      }
    
      .iphone15-pro{
        grid-area: 3/1/4/3;
      }
    }
  }
grid를 이용하여 small screen일 때는 7행 1열, large screen일 때는 5행 2열이 되도록 하였다. 
large screen일 때 ipad-pro, ipad-air, iphone15-pro는 2열을 모두 차지하기 때문에 grid-area 속성을 이용하여 영역을 지정해주었다. 
그리고 카드와 카드 사이의 gap을 지정하였다.
