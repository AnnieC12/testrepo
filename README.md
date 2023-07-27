wiki_covid<- function(){
  wiki_url<-"https://en.wikipedia.org/w/index.php"
  query_param<-list(title="Template:COVID-19_testing_by_country")
  response<-GET(wiki_url,query=query_param)
  return(response)
}
covid19<-wiki_covid()
covid19

root_node <- read_html(covid19)
#root_node
table_node <- html_node(root_node, "table")
table_node
data_table<-html_table(table_node[2])
data_table
covid19_df <-as.data.frame(html_table(table_node))
