#' Obtain the list of categories
#' @description Obtain the list of categories <https://docs.devtodev.com/integration/server-api/labels-api#obtaining-the-list-of-categories>
#' @importFrom httr content POST
#' @importFrom jsonlite toJSON
#'
#' @param user_token User token
#' @param app_id App ID
#'
#' @export

dtd_get_categories <- function(user_token, app_id) {
  categories <- POST("https://www.devtodev.com/api/v1/labels/categories/get",
                     body = toJSON(list("user_token" = user_token,
                                        "app_id" = app_id),
                                   auto_unbox = T))

  if (categories$status_code != 200) {
    stop(paste0("Status code ", categories$status_code, ", Code ", content(categories)$error[[1]]$code,
         ": ", content(categories)$error[[1]]$msg))
  }

  content(categories)$data$categories
}
