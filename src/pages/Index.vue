<template>
  <IndexLayout>
    <div class="container mx-auto px-6 sm:px-0 index-page">
      <div class="post-feed">
 <div class="post-card-custom w-full bg-white">
<Quiz class="my-8 mx-4"/>
  </div>
        <ListItem v-for="edge in $page.entries.edges" :key="edge.node.id" :record="edge.node" />
      </div>

      <div class="pagination flex justify-center mb-8">
        <Pagination
          baseUrl=""
          :currentPage="$page.entries.pageInfo.currentPage"
          :totalPages="$page.entries.pageInfo.totalPages"
          :maxVisibleButtons="5"
          v-if="$page.entries.pageInfo.totalPages > 1"
        />
      </div>
    </div>
  </IndexLayout>
</template>

<page-query>

query($page:Int) {

  entries: allBlog(perPage: 6, page: $page) @paginate {
    totalCount
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        title
        excerpt
        image(width:800)
        path
        timeToRead
        category {
          id
          title
        }
        author {
          id
          name
          image(width:24, height:24, fit:inside)
          path
        }
      }
    }
  }
}

</page-query>

<script>
import ListItem from "~/components/ListItem.vue";
import Pagination from "~/components/Pagination.vue";
import Quiz from "~/components/Quiz.vue";
//import Result from "~/components/Result.vue";


export default {
  metaInfo: {
    title: "Hello, Feres!"
  },
  components: {
    ListItem,
    Pagination,
    Quiz,
//    Result
  }
};
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
