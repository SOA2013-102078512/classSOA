# This file is app/controllers/movies_controller.rb
class MoviesController < ApplicationController
def index
@movies = Movie.all
end
def show
  id = params[:id] # retrieve movie ID from URI route
  @movie = Movie.find(id) # look up movie by unique ID
  # will render app/views/movies/show.html.haml by default
end
def new
  # default: render 'new' template
end

def create
  @movie = Movie.create!(params[:movie])
  redirect_to movies_path
end

def create
  @movie = Movie.create!(params[:movie])
  flash[:notice] = "#{@movie.title} was successfully created."
  redirect_to movies_path
end
 
def edit
  @movie = Movie.find params[:id]
end
 
def update
  @movie = Movie.find params[:id]
  @movie.update_attributes!(params[:movie])
  flash[:notice] = "#{@movie.title} was successfully updated."
  redirect_to movie_path(@movie)
end

def destroy
  @movie = Movie.find(params[:id])
  @movie.destroy
  flash[:notice] = "Movie '#{@movie.title}' deleted."
  redirect_to movies_path
end
  before_filter :authenticate_moviegoer!
end
class MoviesController < ApplicationController
  def movies_with_good_reviews
    @movies = Movie.joins(:reviews).group(:movie_id).
      having('AVG(reviews.potatoes) > 3')
  end
  def movies_for_kids
    @movies = Movie.where('rating in ?', %w(G PG))
  end
end
