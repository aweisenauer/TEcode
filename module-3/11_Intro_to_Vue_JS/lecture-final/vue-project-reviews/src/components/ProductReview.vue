<template>
  <div class="main">
    <h2>Product Reviews for {{ name }}</h2>
    <p class="description">{{ description }}</p>

    <div class="well-display">
    <div class="well">
        <span class="amount">{{averageRating}}</span>
        Average Rating
    </div>

    <div class="well">
        <span class="amount">{{numberOfOneStarReviews}}</span>
        1 Star Review{{numberOfOneStarReviews === 1 ? '' : 's'}}
    </div>

    <div class="well">
        <span class="amount">{{numberOfTwoStarReviews}}</span>
        2 Star Review{{numberOfTwoStarReviews === 1 ? '' : 's'}}
    </div>

    <div class="well">
        <span class="amount">{{numberOfThreeStarReviews}}</span>
        3 Star Review{{numberOfThreeStarReviews === 1 ? '' : 's'}}
    </div>

    <div class="well">
        <span class="amount">{{numberOfFourStarReviews}}</span>
        4 Star Review{{numberOfFourStarReviews === 1 ? '' : 's'}}
    </div>

    <div class="well">
        <span class="amount">{{numberOfFiveStarReviews}}</span>
        5 Star Review{{numberOfFiveStarReviews === 1 ? '' : 's'}}
    </div>
</div>


    <div class="review" v-for="review in reviews" v-bind:key="review.id" v-bind:class="{favorited: review.favorited}">
            <h4>{{ review.reviewer}}</h4>
            <div class="rating">
                <img src="../assets/star.png" class="ratingStar" v-for="ratingNumber in review.rating" v-bind:key="ratingNumber" v-bind:title="review.rating + ' Star Review'"/>
            </div>
            <h3>{{review.title}}</h3>
            <p>{{review.review}}</p>
            <p>Favorite? <input type="checkbox" v-model="review.favorited"/></p>
        </div>
  </div>
</template>

<script>
export default {
  name: "ProductReview",
  data() {
    return {
      name: "Cigar Parties for Dummies",
      description:
        "Host and plan the perfect cigar party for all of your squirrelly friends.",
      reviews: [
        {
          reviewer: "Malcolm Madwell",
          title: "What a book!",
          review:
            "It certainly is a book. I mean, I can see that. Pages kept together with glue and there's writing on it, in some language. Yes indeed, it is a book!",
          rating: 3,
          favorited: false
        },
        {
          reviewer: "Tim Ferriss",
          title: "Had a cigar party started in less than 4 hours.",
          review:
            "It should have been called the four hour cigar party. That's amazing. I have a new idea for muse because of this.",
          rating: 4,
          favorited: false
        },
        {
          reviewer: "Ramit Sethi",
          title: "What every new entrepreneurs needs. A door stop.",
          review:
            "When I sell my courses, I'm always telling people that if a book costs less than $20, they should just buy it. If they only learn one thing from it, it was worth it. Wish I learned something from this book.",
          rating: 1,
          favorited: false
        },
        {
          reviewer: "Gary Vaynerchuk",
          title: "And I thought I could write",
          review:
            "There are a lot of good, solid tips in this book. I don't want to ruin it, but prelighting all the cigars is worth the price of admission alone.",
          rating: 3,
          favorited: false
        },
      ],
      
    };
  },
  computed: {
      averageRating(){
          let sum = this.reviews.reduce((currentSum, review) => {
              return currentSum + review.rating;
          }, 0);
          return sum / this.reviews.length;
      },
      numberOfOneStarReviews(){
          //look at the reviews array, count how many ratings = 1
          return this.reviews.filter((review)=> {
              return review.rating === 1;
          }).length;
      },
       numberOfTwoStarReviews(){
          //look at the reviews array, count how many ratings = 1
          return this.reviews.filter((review)=> {
              return review.rating === 2;
          }).length;
      },
       numberOfThreeStarReviews(){
          //look at the reviews array, count how many ratings = 1
          return this.reviews.filter((review)=> {
              return review.rating === 3;
          }).length;
      },
       numberOfFourStarReviews(){
          //look at the reviews array, count how many ratings = 1
          return this.reviews.filter((review)=> {
              return review.rating === 4;
          }).length;
      },
       numberOfFiveStarReviews(){
          //look at the reviews array, count how many ratings = 1
          return this.reviews.filter((review)=> {
              return review.rating === 5;
          }).length;
      },
  }
};
</script>

<style scoped>
div.main {
  margin: 1rem 0;
}
div.main div.well-display {
    display: flex;
    justify-content: space-around;
}

div.main div.well-display div.well {
    display: inline-block;
    width: 15%;
    border: 1px black solid;
    border-radius: 6px;
    text-align: center;
    margin: 0.25rem;
}

div.main div.well-display div.well span.amount {
    color: darkslategray;
    display: block;
    font-size: 2.5rem;
}

div.main div.review {
    border: 1px black solid;
    border-radius: 6px;
    padding: 1rem;
    margin: 10px;
}

div.main div.review div.rating {
    height: 2rem;
    display: inline-block;
    vertical-align: top;
    margin: 0 0.5rem;
}

div.main div.review div.rating img {
    height: 100%;
}

div.main div.review p {
    margin: 20px;
}

div.main div.review h3 {
    display: inline-block;
}

div.main div.review h4 {
    font-size: 1rem;
}

div.main div.review.favorited{
    background-color: lightyellow;
}

</style>