class MainController < ApplicationController

    def greeting

        render 'landing'

    end

    def kyle

        @ktopthree = ['food', 'sleep', 'anime']


        render 'kyle'

    end

    def will

        @wtopthree = ['guitar', 'records', 'archery']


        render 'will'

    end

    def palindrome

        @string = params[:string]

        (@string.downcase == @string.downcase.reverse) ? @str1 = '<%= @string %> is a palindrome' :  @str1 = '<%= @string %> is not a palindrome'          

        render 'palindrome'

    end

    def madlib

        @noun = params[:noun]
        @verb = params[:verb]
        @adjective = params[:adjective]
        @adverb = params[:adverb]

        render 'madlib'

    end

end
